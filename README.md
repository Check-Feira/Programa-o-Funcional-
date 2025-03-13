# 📘 Programação Funcional no React com TypeScript

Este documento explica como aplicar conceitos de **programação funcional** em um projeto React com TypeScript.
Abaixo estão os principais conceitos abordados, exemplos de código e como encontrá-los em seu projeto.


- ✔ Funções Lambda (Arrow Functions)
- ✔ List Comprehension (map)
- ✔ Closures
- ✔ Funções de Alta Ordem (HOFs)  

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



