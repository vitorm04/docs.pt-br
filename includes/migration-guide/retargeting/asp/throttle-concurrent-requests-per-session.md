### <a name="throttle-concurrent-requests-per-session"></a>Limitação de solicitações simultâneas por sessão

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.6.2 e versões anteriores, o ASP.NET executa solicitações com a mesma Sessionid sequencialmente e sempre emite a Sessionid por meio de um cookie por padrão. Se uma página levar muito tempo para responder, ele prejudicará significativamente o desempenho do servidor simplesmente pressionando F5 no navegador. Na correção, adicionou-se um contador que acompanha as solicitações enfileiradas e encerra as solicitações quando elas excedem um limite especificado. O valor padrão é 50. Se o limite for alcançado, um aviso será registrado no log de eventos e uma resposta HTTP 500 poderá ser registrada no log do IIS.|
|Sugestão|Para restaurar o comportamento antigo, você pode adicionar a seguinte configuração ao arquivo web.config para recusar o novo comportamento.<pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|

