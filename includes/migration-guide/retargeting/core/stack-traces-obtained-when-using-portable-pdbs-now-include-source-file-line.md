### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Os rastreamentos de pilha obtidos ao usar PDBs portáteis agora incluem informações de arquivo de origem e de linha, quando solicitadas

|   |   |
|---|---|
|Detalhes|Começando com o .NET Framework 4.7.2, os rastreamentos de pilha obtidos ao usar PDBs portáteis incluem informações de arquivo de origem e de linha, quando solicitadas. Nas versões anteriores do .NET Framework 4.7.2, as informações de arquivo de origem e de linha não estariam disponíveis ao usar PDBs portáteis, mesmo quando solicitadas explicitamente.|
|Sugestão|Para os aplicativos direcionados ao .NET Framework 4.7.2, você pode recusar as informações de arquivo de origem e de linha ao usar PDBs portáteis, caso não as deseje, adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Para aplicativos direcionados a versões anteriores do .NET Framework mas executados no .NET Framework 4.7.2 ou posterior, você pode aceitar as informações de arquivo de origem e de linha ao usar PDBs portáteis adicionando o seguinte à seção <code>&lt;runtime&gt;</code> do arquivo <code>app.config</code>:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.2|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li>`System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)`<li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

