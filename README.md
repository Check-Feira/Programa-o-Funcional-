# 📘 Programação Funcional no React com TypeScript

Este documento explica como  esta aplicado os  conceitos de **Programação funcional**, nesse  projeto React com TypeScript.
Abaixo estão os seus objetivos, requisitos, forma de instalar, rodar e  claro os principais conceitos abordados como:


- ✔ Funções Lambda (Arrow Functions)
- ✔ List Comprehension (map)
- ✔ Closures
- ✔ Funções de Alta Ordem (HOFs)  

## Objetivos
O presente projeto tem como objetivo o desenvolvimento de uma solução para o controle de fluxo de estoque, na qual visa auxiliar na logística de entrada e saída dos produtos e também na disponibilidade das informações armazenadas. Mediante uma análise junto a comunidade local foi possível identificar uma fragilidade na gestão que usualmente é feita através de planilhas impressas e contagem manual, o que por vezes gera divergência e um retrabalho para atualização consistente das informações reais.

## Requisitos.
#### Requisitos funcionais
- RF01 – O sistema deve cadastrar novo produto
- RF02 – O sistema deve buscar produto
- RF03 – O sistema deve alterar quantidade de produto
- RF04 – O sistema deve gerar relatórios em períodos determinados pelo usuário
#### Requisitos não-funcionais
- RNF01 – O sistema deve ter um tempo de resposta na busca ao produto de 5 segundos
- RNF02 – O sistema deve permitir registro de novos usuários
- RNF03 – O sistema deve atender com bom desempenho acessos simultâneos
- RNF04 – O sistema deve possuir um design responsivo


## 🚀 Deploy
Para instalar as dependências e rodar o projeto, siga os passos abaixo:

1️⃣ Acesse a pasta do projeto

```bash
  cd web
```
2️⃣ Instale as dependências

```bash
  npm  i

```
3️⃣ Inicie o servidor
```bash
 npm  start     
```

## 📌 1. Função Lambda (Arrow Function)
Funções **lambda** são funções anônimas escritas com `=>` (arrow function).

### 📍 Como verificar no projeto:
- Procurar por funções anônimas: `const func = () => {...}`

### 🔹 Exemplo:
```tsx
  const wishlistItems = items.filter(item => 
  item.name.toLowerCase().includes(search.toLowerCase())
);
```
---

## 📌 2. List Comprehension (Uso de .map() para renderizar listas)
Em React, utilizamos `.map()` para percorrer arrays e renderizar elementos dinamicamente.

### 📍 Como verificar no projeto:
- Verificar se listas são renderizadas com `.map()`.
- Dentro do componente, [ WishList.tsx](https://github.com/Check-Feira/CheckFeira/blob/Ingrid/web/src/Components/WishList/WishList.tsx). utilizamos .map() para iterar sobre os itens e renderizar uma tabela.

### 🔹 Exemplo:
```tsx
<tbody>
  {wishlistItems.map((item, index) => (
    <tr className='align-baseline' key={index}>
      <td>{index + 1}</td>
      <td>{item.name}</td>
      <td>{item.price}</td>
      <td>
        <ButtonGroup>
          <Button variant='white' onClick={() => handleEditItem(item?.objectId)}>
            <Image src={iconPencil} />
          </Button>
          <Button variant='white' onClick={() => handleDeleteItem(item?.objectId)}>
            <Image src={iconTrash} />
          </Button>
        </ButtonGroup>
      </td>
    </tr>
  ))}
</tbody>

```
---

## 📌 3. Closure
Uma **closure** ocorre quando uma função "lembra" o escopo onde foi criada, mesmo após esse escopo ter sido finalizado.

### 📍 Como verificar no projeto:
- Buscar por funções que retornam outras funções.

### 🔹 Exemplo:
```tsx
const getWishListItems = async () => {
  try {
    const response = await api.getWishList();
    setItems(response);
  } catch (error) {
    console.error("Error fetching wishlist:", error);
  }
};
```
---

## 📌 4. Funções de Alta Ordem (HOF)
Uma **função de alta ordem** recebe outra função como argumento ou retorna outra função.

### 📍 Como verificar no projeto:
`.O código utiliza funções de alta ordem como .map(), .filter() e .reduce(), além de callbacks para manipulação de eventos:

### 🔹 Exemplo com HOC (Higher Order Component):
```tsx
const handleDeleteItem = async (itemId: string) => {
  try {
    await api.deleteWishList(itemId);
    setItems(prevItems => prevItems.filter(item => item.objectId !== itemId));
  } catch (error) {
    console.error("Error deleting product:", error);
  }
};

```
---

- Todas essas funções de exemplos podem sem encontradas no arquivo  [ WishList.tsx](https://github.com/Check-Feira/CheckFeira/blob/Ingrid/web/src/Components/WishList/WishList.tsx). 





