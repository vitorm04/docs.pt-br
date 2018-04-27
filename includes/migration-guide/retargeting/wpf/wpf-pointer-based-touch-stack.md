### <a name="wpf-pointer-based-touch-stack"></a>Pilha de toque baseada em ponteiro do WPF

|   |   |
|---|---|
|Detalhes|Essa alteração possibilita habilitar uma pilha de toque/caneta do WPF baseada em WM_POINTER opcional.  Desenvolvedores que não habilitarem explicitamente essa opção não deverão ver alterações no comportamento de toque/caneta do WPF. Problemas conhecidos atuais com a pilha de toque/caneta baseada em WM_POINTER opcional:<ul><li>Não há suporte para escrita à tinta em tempo real.</li><li>Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles serão processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</li><li>Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</li><li>A manipulação pode se comportar de maneira diferente</li><li>Arrastar/soltar não mostrará comentários apropriados para entrada por toque</li><li>Isso não afeta entrada de caneta</li><li>Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta</li><li>Isso pode travar o aplicativo até que a entrada do mouse seja detectada.</li><li>Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</li></ul>|
|Sugestão|Desenvolvedores que desejam habilitar essa pilha podem adicionar/mesclar o seguinte ao arquivo app.config do aplicativo:<pre><code class="language-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>Remover isso ou definir o valor como false desativa essa pilha opcional. Observe que a pilha está disponível somente na Atualização do Windows 10 para Criadores e acima.|
|Escopo|Microsoft Edge|
|Versão|4.7|
|Tipo|Redirecionando|

