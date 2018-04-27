### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>Persistência do fluxo de trabalho SQL adiciona clusters de chave primária e não permite valores nulos em algumas colunas

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.7, as tabelas criadas para a SWIS (SQL Workflow Instance Store) pelo script SqlWorkflowInstanceStoreSchema.sql usarão chaves primárias em clusters. Por isso, as identidades não são compatíveis com valores <code>null</code>. A operação da SWIS não é afetada por essa alteração. As atualizações foram feitas serem compatíveis com replicação transacional do SQL Server.|
|Sugestão|O arquivo SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql deve ser aplicado a instalações existentes para usar essa alteração. Novas instalações de banco de dados serão alteradas automaticamente.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Tempo de execução|

