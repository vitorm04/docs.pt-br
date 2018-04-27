### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a>Interrupção de aceitação será revertida de geração de SQL 4.5 diferente para geração de SQL 4.0 mais simples

|   |   |
|---|---|
|Detalhes|As consultas que produzem instruções JOIN e contêm uma chamada para uma operação de limitação sem usar primeiro o OrderBy agora produzem um SQL mais simples. Após a atualização para o .NET Framework 4.5, essas consultas produziram SQLs mais complicados do que as versões anteriores.|
|Sugestão|Esse recurso está desabilitado por padrão. Se Entity Framework gera instruções JOIN adicionais que causam a degradação do desempenho, pode-se habilitar esse recurso adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo (app.config) de configuração da aplicação:<pre><code class="language-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Transparente|
|Versão|4.5.2|
|Tipo|Tempo de execução|

