### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Acessibilidade aprimorada para algumas ferramentas do SDK do .NET

|   |   |
|---|---|
|Detalhes|No SDK do .NET Framework 4.7.1, as ferramentas svcconfigedit.exe e svctraceviewer.exe foram aprimoradas por meio da correção de problemas de acessibilidade variados. A maioria eram problemas pequenos como um nome que não está definido ou certos padrões de automação de interface do usuário implementados incorretamente. Embora muitos usuários não estejam cientes desses valores incorretos, os clientes que usam tecnologias adaptativas como leitores de tela considerarão estas ferramentas de SDK mais acessíveis. Certamente, essas correções alteram alguns comportamentos anteriores, como a ordem do foco do teclado. Para obter todas as correções de acessibilidade nessas ferramentas, é possível adicionar o seguinte ao arquivo app.config:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7.1|
|Tipo|Redirecionando|

