### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF não gera mais para QueryViews com características específicas

|   |   |
|---|---|
|Detalhes|O Entity Framework já não gera uma exceção <xref:System.StackOverflowException?displayProperty=name> quando um aplicativo executa uma consulta que envolve QueryView com uma propriedade de navegação de 0..1 que tenta incluir as entidades relacionadas como parte da consulta. Por exemplo, chamando <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Sugestão|Essa alteração afeta apenas o código que usa relacionamentos de QueryViews com 1-0..1 ao executar consultas que chamam .Include. Isso melhora a confiabilidade e deve ser transparente para quase todos os aplicativos. No entanto, se causa um comportamento inesperado, é possível desabilitá-lo adicionando a seguinte entrada à seção <code>&lt;appSettings&gt;</code> do arquivo de configuração do aplicativo:<pre><code class="language-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.5.2|
|Tipo|Tempo de execução|

