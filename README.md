Curso de Superior de Tecnologia em Análise e Desenvolvimento de Sistemas  
Programação para Internet II  
Prof. Rogério Silva  
Alunos: Juliana Lima, Roniel Dias, Rafael Martins  
<br/><br/>

# Projeto de Diagnóstico: "Controle de Domótica"
<br/><br/>

## 1. Lista de Casos de Uso

### 1.1. Cadastrar Cômodo
O Usuário pode adicionar um novo cômodo à casa

### 1.2. Editar/Excluir Cômodo
O usuário pode modificar ou remover um cômodo existente

### 1.3. Cadastrar Dispositivo
O usuário pode adicionar um dispositivo a um cômodo específico

### 1.4. Editar/Excluir Dispositivo
O usuário pode modificar ou remover um dispositivo

### 1.5. Ligar/Desligar Dispositivo
O usuário pode alternar o estado de um dispositivo entre ligado e desligado.

### 1.6. Visualizar Estado dos Dispositivos
O usuário pode ver quais dispositivos estão ligados ou desligados em cada cômodo

### 1.7. Criar Cena
O usuário pode definir uma sequência de ações com dispositivos, incluindo intervalos.

### 1.8. Editar/Excluir Cena
O usuário pode modificar ou remover uma cena existente

### 1.9. Ativar Cena
O usuário pode executar uma cena, ativando os dispositivos conforme a sequência e intervalos definidos

### 1.10. Desativar Cena
O usuário pode desativar uma cena sem apagá-la
<br/><br/>

## 2. Diagrama de Casos de Uso
![Diagrama de Casos de Uso](https://github.com/rafaelmartins-dev/IFPI-ProjetoDiagnostico_Domotica/blob/main/imagens/diagrama_CasosDeUso.png)
<br/><br/>

## 3. Diagrama de Classes
![Diagrama de Classes](https://github.com/rafaelmartins-dev/IFPI-ProjetoDiagnostico_Domotica/blob/main/imagens/diagrama_Classes.png)
<br/><br/>

## 4. Diagrama Entidade e Relacionamento (DER)
![Diagrama Entidade e Relacionamento](https://github.com/rafaelmartins-dev/IFPI-ProjetoDiagnostico_Domotica/blob/main/imagens/Diagrama_EntidadeRelacionamento.png)
<br/><br/>

## 5. Documentação de API
### 5.1 Criar Cômodo
- **Method:** POST
- **URL:** /api/comodos
- **Body:**
```typescript
{
  "nome": "Sala de Estar"
}
```
- **Response:**
```typescript
{  
  "id": 1,
  "nome": "Sala de Estar"
}
```
- **Status Code:** 200 Ok
<br/><br/>

### 5.2 Listar Cômodo
- **Method:** GET
- **URL:** /api/comodos
- **Response:**
```typescript
[
  { "id": 1, "nome": "Sala de Estar" },
  { "id": 2, "nome": "Cozinha" }
]
```
- **Status Code:** 200 Ok
<br/><br/>


### 5.3. Atualizar Cômodo
- **Method:** PUT
- **URL:** /api/comodos/{id}
- **Body:**
```typescript
{
  "nome": "Sala de Jantar"
}
```
- **Response:**
```typescript
{
  "id": 1,
  "nome": "Sala de Jantar"
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.4. Excluir Cômodo
- **Method:** DELETE
- **URL:** /api/comodos/{id}
- **Response:**
```typescript
{
  "message": "Cômodo excluído com sucesso"
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.5. Criar Dispositivo
- **Method:** POST
- **URL:** /api/dispositivos
- **Body:**
```typescript
{
  "nome": "Lâmpada",
  "comodo_id": 1
}
```
- **Response:**
```typescript
{
  "id": 1,
  "nome": "Lâmpada",
  "estado": false,
  "comodo_id": 1
}
```
- **Status Code:** 201 Created, 400 Bad Request
<br/><br/>


### 5.6. Listar Dispositivos
- **Method:** GET
- **URL:** /api/dispositivos
- **Query Params (Opcional):** ?comodo_id=1
- **Response:**
```typescript
[
  { "id": 1, "nome": "Lâmpada", "estado": false, "comodo_id": 1 }
]
```
- **Status Code:** 200 OK
<br/><br/>


### 5.7. Alternar Estado do Dispositivo
- **Method:** PUT
- **URL:** /api/dispositivos/{id}/alternar
- **Response:**
```typescript
{
  "id": 1,
  "estado": true
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.8. Atualizar Dispositivo
- **Method:** PUT
- **URL:** /api/dispositivos/{id}
- **Body:**
```typescript
{
  "nome": "Ventilador",
  "estado": true,
  "comodo_id": 2
}
```
- **Response:**
```typescript
{
  "id": 1,
  "nome": "Ventilador",
  "estado": true,
  "comodo_id": 2
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.9. Excluir Dispositivo
- **Method:** DELETE
- **URL:** /api/dispositivos/{id}
- **Response:**
```typescript
{
  "message": "Dispositivo excluído com sucesso"
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.10. Criar Cena
- **Method:** POST
- **URL:** /api/cenas
- **Body:**
```typescript
{
  "nome": "Chegar em Casa",
  "ativa": true,
  "acoes": [
    { "dispositivo_id": 1, "ordem": 1, "intervalo": 2 },
    { "dispositivo_id": 2, "ordem": 2, "intervalo": 3 }
  ]
}
```
- **Response:**
```typescript
{
  "id": 1,
  "nome": "Chegar em Casa",
  "ativa": true,
  "acoes": [...]
}
```
- **Status Code:** 201 Created, 400 Bad Request
<br/><br/>


### 5.11. Listar Cenas
- **Method:** GET
- **URL:** /api/cenas
- **Response:**
```typescript
[
  { "id": 1, "nome": "Chegar em Casa", "ativa": true }
]
```
- **Status Code:** 200 OK
<br/><br/>


### 5.12. Execurtar Cena
- **Method:** POST
- **URL:** /api/cenas/{id}/executar
- **Response:**
```typescript
{
  "message": "Cena executada com sucesso"
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.13. Atualizar Cena
- **Method:** PUT
- **URL:** /api/cenas/{id}
- **Body:**
```java
{
    "nome": "Modo Cinema",
    "ativa": false,
    "acoes": [...]
}
```
- **Response:**
```typescript
{
  "id": 1,
  "nome": "Modo Cinema",
  "ativa": false
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>


### 5.14. Excluir Cena
- **Method:** DELETE
- **URL:** /api/cenas/{id}
- **Response:**
```typescript
{
  "message": "Cena excluída com sucesso"
}
```
- **Status Code:** 200 OK, 404 Not Found
<br/><br/>
