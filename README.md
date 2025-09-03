Curso de Superior de Tecnologia em Análise e Desenvolvimento de Sistemas  
Programação para Internet II  
Prof. Rogério Silva  
Alunos: Juliana Lima, Roniel Dias, Rafael Martins  
<br/><br/>

# Projeto de Diagnóstico: "Controle de Domótica"
<br/><br/>

## Lista de Casos de Uso

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
```python
{  
  "id": 1,
  "nome": "Sala de Estar"
}
```
- **Status Code:** 200 Ok