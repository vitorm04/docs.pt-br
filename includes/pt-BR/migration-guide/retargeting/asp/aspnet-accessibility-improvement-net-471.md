### <a name="aspnet-accessibility-improvement-in-net-471"></a>Melhoria de acessibilidade do ASP.NET no .NET 4.7.1

|   |   |
|---|---|
|Detalhes|O ASP.NET está melhorando o funcionamento dos controles Web ASP.NET com a tecnologia de acessibilidade no Visual Studio para melhor suporte a clientes ASP.NET.  Isso inclui as seguintes alterações:<ul><li>Alterações para implementar padrões de acessibilidade de interface do usuário ausentes em controles, como a caixa de diálogo Adicionar Campo no assistente de Exibição de Detalhes.</li><li>Alterações para melhorar a exibição no modo de Alto Contraste, como o Editor de Campos do Pager de Dados.</li><li>Alterações para melhorar as experiências de navegação pelo teclado para controles, como a Kanela Configurar Contexto de Objeto ou Janela Configurar Fonte de Dados.</li></ul>|
|Sugestão|**Como aceitar ou recusar essas alterações** Para se beneficiar dessas alterações, o Designer do Visual Studio deverá ser executado no .NET Framework 4.7.1 ou posterior. O aplicativo Web pode se beneficiar dessas alterações de uma das seguintes maneiras:<ul><li>Instalar o Visual Studio 2017 15.3 ou posterior, que dá suporte a novas funcionalidades de acessibilidade com a seguinte opção de AppContext por padrão.</li><li>Recuse os comportamentos de acessibilidade herdados adicionando a Opção de AppContext **Switch.UseLegacyAccessibility** à seção `<runtime>` do arquivo devenv.exe.config e configurando-a como `false`, como mostra o exemplo a seguir.</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|Escopo|Secundário|
|Versão|4.7.1|
|Tipo|Redirecionando|
