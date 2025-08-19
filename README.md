## Pré-requisitos
- Uma assinatura do Azure (ou criar uma conta gratuita);
- Permissões adequadas:
  - Função de **Contribuidor** da Instância Gerenciada de SQL atribuída;
  - Permissão `Microsoft.Sql/managedInstances/write` se provisionar em sub-rede delegada;
- Módulo **Az.SQL** atualizado no PowerShell ou CLI do Azure.

## Criando a Instância Gerenciada de SQL

### 1. Acesso ao Portal do Azure
1. Entre no [Portal do Azure](https://portal.azure.com).  
2. No menu esquerdo, selecione **SQL do Azure** ou pesquise **SQL do Azure** em **Todos os serviços**.  
3. Clique em **+ Criar** e selecione **Instâncias Gerenciadas de SQL → Criar**.  

---

### 2. Guia Básico
Preencha os campos obrigatórios:

| Configuração                  | Valor sugerido           | Descrição |
|--------------------------------|------------------------|-----------|
| Assinatura                     | Sua assinatura          | Permissão para criar recursos |
| Grupo de recursos              | Novo ou existente       | Para organização dos recursos |
| Nome da instância gerenciada   | Qualquer nome válido    | Regras de nomenclatura do Azure |
| Região                          | Escolher região         | Regiões suportadas do Azure |
| Pertence a um pool de instâncias? | Sim ou Não            | Criar dentro de um pool de instâncias |
| Método de autenticação          | SQL                     | Autenticação SQL ou Microsoft Entra |
| Logon do administrador         | Nome válido             | Não usar serveradmin |
| Senha                           | Senha forte             | Mínimo 16 caracteres |

#### Computação + Armazenamento
| Configuração           | Valor sugerido         | Descrição |
|------------------------|----------------------|-----------|
| Camada de serviço      | Uso Geral             | Adequada para a maioria das cargas de produção |
| Geração do hardware    | Standard (Gen5)       | Define limites de CPU e memória |
| vCores                 | Número definido       | Recursos de computação provisionados |
| Armazenamento em GB    | Definir conforme necessidade | Tamanho do banco de dados |
| Licença SQL Server     | Selecionar aplicável  | Pagamento conforme uso ou existente |
| Redundância backup     | Geográfica             | Armazenamento de backup seguro |

Clique em **Aplicar** para salvar e prossiga para a guia **Rede**.

---

### 3. Guia Rede
| Configuração                   | Valor sugerido        | Descrição |
|--------------------------------|---------------------|-----------|
| Rede virtual / sub-rede         | Criar ou existente  | Modificar se necessário |
| Tipo de conexão                 | Selecionar adequado | Serviços do Azure, Internet ou Sem acesso |
| Ponto de extremidade público    | Desabilitar          | Permite acesso externo se habilitado |
| Permitir acesso                 | Sem acesso           | Define regras de segurança |

---

### 4. Guia Segurança
- Para início rápido, mantenha as configurações padrão.  

---

### 5. Configurações Adicionais
| Configuração                 | Valor sugerido         | Descrição |
|-------------------------------|----------------------|-----------|
| Ordenação                     | Escolher compatível  | Igual à ordenação do SQL Server de origem |
| Fuso horário                   | Definir adequado     | Timezone da instância |
| Replicação geográfica         | Não                  | Somente se usar failover |
| Janela de manutenção           | Definir janela       | Horário para manutenção planejada |

---

### 6. Marcação
- Adicione **tags** para identificar o proprietário e o ambiente (Ex.: Produção, Desenvolvimento).

---

### 7. Revisar + Criar
- Clique em **Examinar + criar** e revise todas as escolhas.  
- Clique em **Criar** para implantar a instância.

---

### 8. Monitoramento
- Use o **ícone Notificações** para verificar o progresso da implantação.  
- Após a conclusão, navegue até o **grupo de recursos** para acessar a instância.  

#### Dica
Se o navegador for fechado, o provisionamento pode ser monitorado pelo **portal, PowerShell ou CLI do Azure**.

---

### 9. Revisão de Rede
- Verifique **Tabela de rotas** e **Regras de Segurança** (entrada e saída) no grupo de segurança.

---

### 10. Criar Banco de Dados
1. Acesse a instância no portal do Azure.  
2. Clique em **+ Novo banco de dados**.  
3. Configure nome, fonte de dados (vazio ou backup), e demais parâmetros.  
4. Clique em **Revisar + criar → Criar**.

---

### 11. Recuperar Detalhes de Conexão
- Na guia **Visão Geral**, copie o **Host/FQDN** para se conectar à instância.  
- Exemplo: `nome_do_seu_host.a1b2c3d4e5f6.database.windows.net`

---

### Referências
- [Documentação Oficial do Azure](https://learn.microsoft.com/pt-br/azure/)
- [Início Rápido: Instância Gerenciada de SQL do Azure](https://learn.microsoft.com/pt-br/azure/azure-sql/managed-instance/)
