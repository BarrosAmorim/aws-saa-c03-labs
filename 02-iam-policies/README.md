# Projeto 02 - IAM - Políticas Gerenciadas e Personalizadas

Documentação do laboratório desenvolvido durante os estudos para a certificação **AWS Certified Solutions Architect – Associate (SAA-C03)**.

---

## Sobre este projeto

Este laboratório apresenta os diferentes tipos de políticas do **AWS Identity and Access Management (IAM)**, demonstrando como criar e gerenciar permissões utilizando o Console de Gerenciamento da AWS.

Durante o laboratório foram exploradas as políticas gerenciadas pela AWS (**AWS Managed Policies**), criada uma política gerenciada pelo cliente (**Customer Managed Policy**) utilizando o **Visual Editor** e criada uma **Inline Policy** para compreender suas diferenças e aplicações.

---

## Índice

- [Objetivo](#objetivo)
- [Serviços utilizados](#serviços-utilizados)
- [Conceitos abordados](#conceitos-abordados)
- [Pré-requisitos](#pré-requisitos)
- [Arquitetura](#arquitetura)
- [Passo 1 - Criando uma Customer Managed Policy](#passo-1---criando-uma-customer-managed-policy)
- [Passo 2 - Criando uma Inline Policy](#passo-2---criando-uma-inline-policy)
- [Passo 3 - Comparando os tipos de políticas](#passo-3---comparando-os-tipos-de-políticas)
- [Resultado Final](#resultado-final)
- [Conhecimentos adquiridos](#conhecimentos-adquiridos)
- [Boas práticas aplicadas](#boas-práticas-aplicadas)
- [Referências](#referências)

---

## Objetivo

Compreender o funcionamento das políticas do **AWS Identity and Access Management (IAM)**, explorando os diferentes tipos de políticas disponíveis, suas características e aplicações práticas no controle de acesso aos recursos da AWS.

---

## Serviços utilizados

- AWS Identity and Access Management (IAM)

---

## Conceitos abordados

- IAM Policies
- AWS Managed Policies
- Customer Managed Policies
- Inline Policies
- Visual Editor
- JSON Policy Document
- IAM Permissions
- Principle of Least Privilege (Princípio do Menor Privilégio)

---

## Pré-requisitos

- Conta AWS ativa.
- Projeto 01 concluído.
- Usuário IAM **Barros** criado.
- Usuário **Barros** pertencente ao grupo **Administrators**.
- MFA habilitado para o usuário **Barros**.

---

## Arquitetura

Neste laboratório foi utilizado o usuário administrador criado no projeto anterior para estudar os diferentes tipos de políticas disponíveis no IAM.

```text
                 AWS Account
                      │
                      ▼
              IAM User (Barros)
                      │
                      ▼
          AdministratorAccess
                      │
      ┌───────────────┼────────────────┐
      │               │                │
      ▼               ▼                ▼
AWS Managed     Customer Managed    Inline Policy
   Policy            Policy
```

---

## Passo 1 - Criando uma Customer Managed Policy

Foi criada uma política gerenciada pelo cliente (**Customer Managed Policy**) utilizando o **Visual Editor** do AWS IAM.

As **Customer Managed Policies** permitem que administradores criem conjuntos de permissões personalizados para atender necessidades específicas da organização, oferecendo maior flexibilidade em comparação às políticas gerenciadas pela AWS.

Durante a criação da política foi possível selecionar o serviço, definir as ações permitidas e revisar as permissões antes de concluir sua criação.

Embora a política tenha sido criada utilizando o editor visual, o IAM gera automaticamente um documento JSON equivalente para representar as permissões configuradas.

### Evidência

![Customer Managed Policy](screenshots/01-create-policy.png)

---

## Passo 2 - Criando uma Inline Policy

Foi criada uma **Inline Policy** diretamente no usuário **Barros** utilizando o **Visual Editor** do IAM.

As **Inline Policies** permanecem vinculadas exclusivamente ao usuário, grupo ou role onde foram criadas, não podendo ser reutilizadas em outros recursos.

Esse tipo de política é recomendado apenas quando uma permissão deve existir exclusivamente para um único recurso.

Após compreender seu funcionamento, a política foi removida para manter o ambiente organizado.

### Evidência

![Inline Policy](screenshots/02-inline-policy.png)

---

## Passo 3 - Comparando os tipos de políticas

Durante este laboratório foram analisados os três principais tipos de políticas disponíveis no IAM.

| Tipo de política        | Criada pela AWS | Reutilizável | Principal utilização                                                  |
| ----------------------- | --------------- | ------------ | --------------------------------------------------------------------- |
| AWS Managed Policy      | Sim             | Sim          | Políticas mantidas pela AWS para cenários comuns.                     |
| Customer Managed Policy | Não             | Sim          | Políticas criadas pelo cliente para atender necessidades específicas. |
| Inline Policy           | Não             | Não          | Políticas exclusivas de um único usuário, grupo ou role.              |

Embora o **Visual Editor** facilite a criação das políticas, todas elas são armazenadas internamente pela AWS como documentos JSON.

Os principais elementos de uma política IAM são:

| Elemento  | Descrição                                                     |
| --------- | ------------------------------------------------------------- |
| Version   | Define a versão da linguagem de políticas da AWS.             |
| Statement | Conjunto de regras que compõem a política.                    |
| Effect    | Define se a ação será permitida (`Allow`) ou negada (`Deny`). |
| Action    | Lista das ações permitidas ou negadas.                        |
| Resource  | Recursos aos quais a política será aplicada.                  |

---

## Resultado Final

Ao concluir este laboratório foi possível compreender os principais mecanismos utilizados pelo IAM para controle de permissões, identificando quando utilizar cada tipo de política e como elas são representadas internamente pela AWS.

As seguintes atividades foram realizadas:

- Exploração das AWS Managed Policies disponíveis no IAM.
- Criação de uma Customer Managed Policy utilizando o Visual Editor.
- Criação de uma Inline Policy.
- Comparação entre os diferentes tipos de políticas do IAM.
- Compreensão da estrutura interna das políticas em formato JSON.

---

## Conhecimentos adquiridos

Ao finalizar este laboratório foram consolidados os seguintes conhecimentos:

- Funcionamento das políticas do IAM.
- Diferenças entre AWS Managed Policies, Customer Managed Policies e Inline Policies.
- Utilização do Visual Editor para criação de políticas.
- Estrutura básica dos documentos JSON utilizados pelo IAM.
- Aplicação do princípio do menor privilégio (Principle of Least Privilege).
- Importância da reutilização de políticas para facilitar a administração de permissões.

---

## Boas práticas aplicadas

Durante este laboratório foram seguidas as seguintes recomendações da AWS:

- Utilizar políticas reutilizáveis sempre que possível.
- Criar permissões específicas para cada necessidade.
- Evitar conceder privilégios além do necessário.
- Aplicar o princípio do menor privilégio (Least Privilege).
- Preferir Customer Managed Policies em vez de Inline Policies quando houver possibilidade de reutilização.
- Revisar periodicamente as permissões concedidas aos usuários e grupos.
- Documentar todas as configurações realizadas.

---

## Referências

- AWS Identity and Access Management User Guide
- IAM Policies
- IAM JSON Policy Elements Reference
- AWS Security Best Practices
