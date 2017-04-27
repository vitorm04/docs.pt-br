---
title: "Diagnóstico de Compatibilidade do .NET | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e481270-b62a-4cb4-8dda-5b4c5b59d61d
caps.latest.revision: 7
author: twsouthwick
ms.author: tasou
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 19006cc5f24ffc66b92e53e8174c6bd33c249679
ms.openlocfilehash: 06ebf87e02c8fd745d9c2f3a55eca329323a7d91
ms.lasthandoff: 04/18/2017

---
# <a name="net-compatibility-diagnostics"></a>Diagnóstico de Compatibilidade do .NET
O Diagnóstico de Compatibilidade do .NET são analisadores capacitados pelo Roslyn que ajudam a identificar problemas de compatibilidade de aplicativos entre versões do .NET Framework. Esta lista contém todos os analisadores disponíveis, embora apenas um subconjunto seja aplicado a qualquer migração específica. Os analisadores determinarão quais problemas se aplicam à migração planejada e os trará à tona. Para problemas divididos por versões afetadas, confira: [Compatibilidade de aplicativos](../../../docs/framework/migration-guide/application-compatibility.md).  
  
 Cada problema inclui as seguintes informações:  
  
-   A descrição do que mudou em relação a uma versão anterior.  
  
-   A sugestão é uma descrição de como a alteração afeta os clientes e se alguma solução alternativa está disponível para preservar a compatibilidade entre versões.  
  
-   Uma avaliação da importância da alteração. O problema de compatibilidade de aplicativos é categorizado como se segue:  
  
    |||  
    |-|-|  
    |Principal|Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código.|  
    |Secundário|Uma alteração que afeta um pequeno número de aplicativos ou que exige modificação secundária do código.|  
    |Caso de borda|Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.|  
    |Transparente|Uma alteração que não afeta visivelmente o desenvolvedor nem o usuário do aplicativo.|  
  
-   A versão indica quando a alteração aparece pela primeira vez na estrutura. Algumas das alterações são revertidas, e isso também é indicado.  
  
-   O tipo de alteração:  
  
    |||  
    |-|-|  
    |Redirecionando|A alteração afeta aplicativos que são recompilados para uma nova versão do .NET Framework.|  
    |Tempo de execução|A alteração afeta um aplicativo existente que se destina a uma versão anterior do .NET Framework, mas é executado em uma versão posterior.|  
  
-   As APIs afetadas, se houver.  
  
-   As IDs do diagnóstico disponível  
  
<a name="diagnostic1"></a>   
## <a name="1-soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>1: SoapFormatter não pode desserializar Hashtable e objetos de coleção ordenados semelhantes  
  
|||  
|-|-|  
|Detalhes|O SoapFormatter não garante que objetos serializados em uma versão do .NET Framework serão desserializados com êxito em uma versão diferente. Especificamente, algumas coleções ordenadas (como Hashtable) adicionaram membros entre 4.0 e 4.5, de modo que tais objetos desses tipos não podem ser desserializados com o .NET 4.0 se tiverem sido serializados com o .NET 4.5. Observe que se os dados serializados forem serializados e desserializados com a mesma versão do .NET Framework, nenhum problema ocorrerá.|  
|Sugestão|A serialização SoapFormatter deve ser substituída pela serialização BinaryFormatter ou NetDataContractSerialization para ser resiliente às mudanças do .NET Framework.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize%28System.IO.Stream%2CSystem.Runtime.Remoting.Messaging.HeaderHandler%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize%28System.IO.Stream%2CSystem.Object%2CSystem.Runtime.Remoting.Messaging.Header%5B%5D%29?displayProperty=fullName>|  
|Analisadores|CD0001B<br /><br /> CD0001A|  
  
<a name="diagnostic3"></a>   
## <a name="3-wpf-datatemplate-elements-are-now-visible-to-uia"></a>3: Os elementos DataTemplate do WPF agora são visíveis à UIA  
  
|||  
|-|-|  
|Detalhes|Anteriormente, os elementos DataTemplate eram invisíveis à Automação da Interface do Usuário. A partir da versão 4.5, a Automação da Interface do Usuário detectar esses elementos. Isso é útil em muitos casos, mas pode arruinar os testes que dependem das árvores UIA que não contêm elementos DataTemplate.|  
|Sugestão|Os testes de Automação da Interface do Usuário para esse aplicativo talvez precisem ser atualizados para contabilizar a árvore UIA agora, incluindo elementos DataTemplate anteriormente invisíveis. Por exemplo, os testes que esperam que alguns elementos fiquem próximos uns dos outros agora podem precisar esperar elementos UIA anteriormente invisíveis entre eles. Ou os testes que dependem de determinadas contagens ou de índices para elementos UIA talvez precisem ser atualizados com novos valores.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.DataTemplate.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Windows.DataTemplate.%23ctor%28System.Object%29?displayProperty=fullName>|  
|Analisadores|CD0003|  
  
<a name="diagnostic4"></a>   
## <a name="4-wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>4: O texto selecionado TextBox do WPF aparece em cor diferente quando a caixa de texto está inativa  
  
|||  
|-|-|  
|Detalhes|No .NET 4.5, quando um controle de caixa de texto do WPF estiver inativo (não tem foco), o texto selecionado dentro da caixa aparecerá em uma cor diferente de quando o controle estiver ativo.|  
|Sugestão|O comportamento anterior (.NET 4.0) pode ser restaurado definindo a propriedade [FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported](https://msdn.microsoft.com/library/system.windows.frameworkcompatibilitypreferences.areinactiveselectionhighlightbrushkeyssupported\(v=vs.110\).aspx) como false.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analisadores|CD0004|  
  
<a name="diagnostic5"></a>   
## <a name="5-listtforeach-can-throw-exception-when-modifying-list-item"></a>5: List\<T>.ForEach agora gera exceção durante a modificação de item de lista  
  
|||  
|-|-|  
|Detalhes|A partir do .NET 4.5, o enumerador `List<T>.ForEach` vai gerar uma exceção InvalidOperationException se um elemento na coleção de chamada for modificado. Anteriormente, isso não geraria uma exceção, mas podia levar a condições de corrida.|  
|Sugestão|De modo ideal, o código deve ser corrigido para não modificar listas durante a enumeração de seus elementos, pois essa nunca é uma operação segura. Porém, para reverter para o comportamento anterior, um aplicativo pode ser direcionado para o .NET 4.0.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Collections.Generic.List%601.ForEach%28System.Action%7B%600%7D%29?displayProperty=fullName>|  
|Analisadores|CD0005|  
  
<a name="diagnostic6"></a>   
## <a name="6-systemuri-parsing-adheres-to-rfc-3987"></a>6: A análise de System.Uri adere à RFC 3987  
  
|||  
|-|-|  
|Detalhes|A análise de URI foi alterada de várias maneiras no .NET 4.5. No entanto, observe que essas alterações afetam apenas o código que se destinam ao NET 4.5. Se um binário for destinado ao .NET 4.0, o comportamento antigo será observado. As alterações na análise de URI no .NET 4.5 incluem:<br /><br /> A análise de URI executará a normalização e a verificação de caracteres de acordo com as regras recentes de URI na RFC 3987<br /><br /> O formulário C de normalização Unicode só será executado na parte de host do URI<br /><br /> Agora, os URIs mailto: inválidos vão gerar uma exceção<br /><br /> Os pontos à direita no fim de um segmento de caminho agora são preservados<br /><br /> Os URIs `file://` não escapam o caractere `?`<br /><br /> Os caracteres de controle Unicode `U+0080` a `U+009F` não têm suporte<br /><br /> Os caracteres de vírgula `,` ou `%2c` não fogem ao escape automaticamente|  
|Sugestão|Se a semântica de análise de URI antiga do .NET 4.0 for necessária (geralmente não é), ela poderá ser usada visando o .NET 4.0. Isso pode ser feito usando um TargetFrameworkAttribute no assembly ou pela interface de usuário do sistema do projeto no Visual Studio, na página "propriedades do projeto".|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Uri.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29?displayProperty=fullName><br /><br /> <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.String%2CSystem.UriKind%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.String%2CSystem.Uri%40%29?displayProperty=fullName><br /><br /> <xref:System.Uri.TryCreate%28System.Uri%2CSystem.Uri%2CSystem.Uri%40%29?displayProperty=fullName>|  
|Analisadores|CD0006D<br /><br /> CD0006C<br /><br /> CD0006F<br /><br /> CD0006E<br /><br /> CD0006A<br /><br /> CD0006G<br /><br /> CD0006B|  
  
<a name="diagnostic10"></a>   
## <a name="10-systemuri-escaping-now-supports-rfc-3986-httptoolsietforghtmlrfc3986"></a>10: Escape de System.Uri agora dá suporte à RFC 3986 (http://tools.ietf.org/html/rfc3986)  
  
|||  
|-|-|  
|Detalhes|O escape do URI mudou no .NET 4.5 para dar suporte à [RFC 3986](http://tools.ietf.org/html/rfc3986). As alterações específicas incluem:<br /><br /> `EscapeDataString` escapa caracteres reservados com base na RFC 3986.<br /><br /> `EscapeUriString` não escapa caracteres reservados.<br /><br /> `UnescapeDataString` não gerará uma exceção se encontrar uma sequência de escape inválida.<br /><br /> Os caracteres escapados não reservados não são escapados.|  
|Sugestão|Atualize os aplicativos para não dependerem da geração de UnescapeDataString no caso de uma sequência de escape inválida. Essas sequências devem ser detectadas diretamente agora.<br /><br /> Da mesma forma, espere que o URI com escape e sem escape, bem como cadeias de caracteres de dados, possam variar do .NET 4.0 e .NET 4.5, não devendo ser comparados entre as versões do .NET diretamente. Em vez disso, eles devem ser analisados e normalizados em uma única versão do .NET antes que qualquer comparação seja feita.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Uri.EscapeDataString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.EscapeUriString%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Uri.UnescapeDataString%28System.String%29?displayProperty=fullName>|  
|Analisadores|CD0010A<br /><br /> CD0010B<br /><br /> CD0010C|  
  
<a name="diagnostic11"></a>   
## <a name="11-systemnetpeertopeercollaboration-unavailable-on-windows-8"></a>11: System.Net.PeerToPeer.Collaboration não disponível no Windows 8  
  
|||  
|-|-|  
|Detalhes|O namespace System.Net.PeerToPeer.Collaboration não está disponível no Windows 8 ou superior.|  
|Sugestão|Os aplicativos que dão suporte ao Windows 8 ou superior devem ser atualizados para não dependerem desse namespace ou de seus membros.|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Net.PeerToPeer.Collaboration?displayProperty=fullName>|  
|Analisadores|CD0011|  
  
<a name="diagnostic12"></a>   
## <a name="12-mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>12: Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto XmlSerializer). Tentar serializar um catálogo de MEF gera uma exceção.|  
|Sugestão|Não é mais possível usar o MEF para criar um serializador|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0012|  
  
<a name="diagnostic13"></a>   
## <a name="13-missing-target-framework-moniker-results-in-40-behavior"></a>13: Ausência de Moniker de Estrutura de Destino resulta no comportamento da versão 4.0  
  
|||  
|-|-|  
|Detalhes|Os aplicativos sem um [TargetFrameworkAttribute](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) aplicado no nível de assembly serão executados automaticamente usando a semântica (quirks) do .NET Framework 4.0. Para garantir a alta qualidade, é aconselhável que todos os binários sejam explicitamente atribuídos a um TargetFrameworkAttribute, indicando a versão do .NET Framework com a qual eles foram criados. Observe que usar um moniker de estrutura de destino em um arquivo de projeto fará com que o MSBuild aplique automaticamente um TargetFrameworkAttribute.|  
|Sugestão|O [atributo de estrutura de destino](https://msdn.microsoft.com/library/system.runtime.versioning.targetframeworkattribute\(v=vs.110\).aspx) deve ser fornecido, seja por meio da adição do atributo diretamente ao assembly ou da especificação de uma estrutura de destino no [arquivo de projeto, seja por meio da GUI das propriedades do projeto do Visual Studio](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx).|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0013|  
  
<a name="diagnostic14"></a>   
## <a name="14-no-longer-able-to-set-enableviewstatemac-to-false"></a>14: Não é mais possível definir EnableViewStateMac como false  
  
|||  
|-|-|  
|Detalhes|O ASP.NET não permite mais que os desenvolvedores especifiquem `<pages enableViewStateMac="false"/>` ou `<@Page EnableViewStateMac="false" %>`. O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido. Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como false são afetados.|  
|Sugestão|EnableViewStateMac deve ser considerada como true e qualquer erro MAC resultante deverá ser resolvido (conforme explicado [nestas](https://support.microsoft.com/kb/2915218) diretrizes, que contêm várias resoluções que variam de acordo com as características do que está causando os erros MAC).|  
|Escopo|Principal|  
|Versão|4.5.2|  
|Tipo|Tempo de execução|  
|Analisadores|CD0014|  
  
<a name="diagnostic18"></a>   
## <a name="18-blockingcollectionttrytakefromany-does-not-throw-anymore"></a>18: BlockingCollection\<T>.TryTakeFromAny não é mais gerado  
  
|||  
|-|-|  
|Detalhes|Se uma das coleções de entrada for marcada como concluída, `BlockingCollection<T>.TryTakeFromAny(BlockingCollection<T>[], T)` não retornará mais -1 e `BlockingCollection<T>.TakeFromAny` não vai mais gerar uma exceção. Essa alteração possibilita trabalhar com coleções quando uma das coleções está vazia ou concluída, mas a outra coleção ainda possui itens que podem ser recuperados.|  
|Sugestão|Se o retorno de -1 de TryTakeFromAny ou a geração de TakeFromAny foram usados para fins de fluxo de controle no caso de conclusão de uma coleção de blocos, tal código agora deverá ser alterado para usar `.Any(b => b.IsCompleted)` a fim de detectar essa condição.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny%28System.Collections.Concurrent.BlockingCollection%7B%600%7D%5B%5D%2C%600%40%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analisadores|CD0018A<br /><br /> CD0018B|  
  
<a name="diagnostic19"></a>   
## <a name="19-xmlschemaexception-now-sets-line-positions-properly"></a>19: XmlSchemaException agora define posições de linhas corretamente  
  
|||  
|-|-|  
|Detalhes|Se o valor de LoadOptions.SetLineInfo for passado para o método Load e ocorrer um erro de validação, as propriedades XmlSchemaException.LineNumber e XmlSchemaException.LinePosition agora conterão informações de linha.|  
|Sugestão|O código de tratamento de exceção que supõe que XmlSchemaException.LineNumber e XmlSchemaException.LinePosition não serão definidas deverá ser atualizado, uma vez que essas propriedades agora serão definidas corretamente quando SetLineInfo for usado durante o carregamento de XML.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Xml.Linq.LoadOptions?displayProperty=fullName>|  
|Analisadores|CD0019|  
  
<a name="diagnostic20"></a>   
## <a name="20-systemactivities-is-now-aptca"></a>20: System.Activities agora é APTCA  
  
|||  
|-|-|  
|Detalhes|O assembly é marcado com o atributo AllowPartiallyTrustedCallersAttribute.|  
|Sugestão|As classes derivadas não podem ser marcadas com o SecurityCriticalAttribute. Antigamente, os tipos derivados tinham que ser marcados com o SecurityCriticalAttribute. No entanto, essa mudança não deve ter um impacto real.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0020|  
  
<a name="diagnostic21"></a>   
## <a name="21-workflow-30-types-are-obsolete"></a>21: Os tipos do WorkFlow 3.0 estão obsoletos  
  
|||  
|-|-|  
|Detalhes|As APIs (aquelas do namespace System.Workflow) do WWF (Windows Workflow Foundation) 3.0 agora estão obsoletas.|  
|Sugestão|Agora devem ser usadas as novas APIs (em System.Activities) do WWF 4.0. Um exemplo de como usar as novas APIs pode ser encontrado [aqui](https://msdn.microsoft.com/library/jj205427.aspx), e outras diretrizes estão disponíveis [aqui](http://blogs.msdn.com/b/workflowteam/archive/2012/02/08/deprecatingwf3.aspx). Como alternativa, uma vez que as APIs do WWF 3.0 ainda têm suporte, elas poderão ser usadas, e o aviso de hora da compilação deve ser evitado suprimindo-o ou usando um compilador mais antigo.|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|Analisadores|CD0021|  
  
<a name="diagnostic22"></a>   
## <a name="22-some-workflow-drag-and-drop-apis-are-obsolete"></a>22: Algumas APIs arrastar e soltar do Fluxo de Trabalho estão obsoletas  
  
|||  
|-|-|  
|Detalhes|A API Arrastar/Soltar do Fluxo de Trabalho está obsoleta e vai gerar avisos do compilador se o aplicativo for recompilado na versão 4.5.|  
|Sugestão|No lugar, devem ser usadas as novas APIs [DragDropHelper](https://msdn.microsoft.com/library/system.activities.presentation.dragdrophelper\(v=vs.110\).aspx) que dão suporte a operações com vários objetos. Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo. Ainda há suporte para as APIs.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%28System.Windows.DragEventArgs%29?displayProperty=fullName><br /><br /> <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%28System.Windows.DependencyObject%2CSystem.Windows.DragEventArgs%2CSystem.Activities.Presentation.EditingContext%29?displayProperty=fullName>|  
|Analisadores|CD0022|  
  
<a name="diagnostic23"></a>   
## <a name="23-new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a>23: Sobrecargas novas (ambíguas) do Dispatcher.Invoke podem resultar em comportamento diferente  
  
|||  
|-|-|  
|Detalhes|O .NET Framework 4.5 adiciona novas sobrecargas ao Dispatcher.Invoke que incluem um parâmetro do tipo System.Action. Quando um código existente é recompilado, os compiladores podem resolver as chamadas aos métodos Dispatcher.Invoke que têm um parâmetro Delegate como chamadas aos métodos Dispatcher.Invoke com um parâmetro System.Action. Se uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro Delegate for resolvida como uma chamada à sobrecarga do Dispatcher.Invoke com um parâmetro System.Action, poderão ocorrer as seguintes diferenças no comportamento:<br /><br /> Se ocorrer uma exceção, os eventos Dispatcher.UnhandledExceptionFilter e Dispatcher.UnhandledException não serão gerados. Em vez disso, as exceções serão tratadas pelo evento UnobservedTaskException.<br /><br /> As chamadas a alguns membros, como DispatcherOperation.Result, serão bloqueadas até que a operação tenha sido concluída.|  
|Sugestão|Para evitar ambiguidade (e possíveis diferenças no tratamento de exceções ou nos comportamentos de bloqueio), a chamada ao código Dispatcher.Invoke pode passar um object[] vazio como um segundo parâmetro à chamada Invoke a fim de garantir a resolução para a sobrecarga do método no .NET 4.0.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.TimeSpan%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Windows.Threading.Dispatcher.Invoke%28System.Delegate%2CSystem.Windows.Threading.DispatcherPriority%2CSystem.Object%5B%5D%29?displayProperty=fullName>|  
|Analisadores|CD0023|  
  
<a name="diagnostic24"></a>   
## <a name="24-encoderparameter-ctor-is-obsolete"></a>24: O construtor EncoderParameter está obsoleto  
  
|||  
|-|-|  
|Detalhes|O construtor `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` agora está obsoleto e introduzirá novos avisos de compilação se for usado.|  
|Sugestão|Embora o construtor `EncoderParameter.EncoderParameter(Encoder, Int32, Int32, Int32)` continue funcionando, o seguinte construtor deverá ser usado no lugar para evitar o aviso de compilação obsoleta durante a recompilação de código com as ferramentas do .NET 4.5: [EncoderParameter.EncoderParameter(Encoder, Int32, EncoderParameterValueType, IntPtr)](https://msdn.microsoft.com/library/hh875096\(v=vs.110\).aspx).|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analisadores|CD0024|  
  
<a name="diagnostic26"></a>   
## <a name="26-change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>26: Mudança no comportamento dos métodos Task.WaitAll com argumentos de tempo limite  
  
|||  
|-|-|  
|Detalhes|O comportamento de Task.WaitAll tornou-se mais consistente no .NET 4.5.<br /><br /> No .NET Framework 4, esses métodos se comportavam de maneira inconsistente. Quando o tempo limite expirava, se uma ou mais tarefas estivessem concluídas ou tivessem sido canceladas antes da chamada de método, o método gerava uma exceção AggregateException. Quando o tempo limite expirava, se nenhuma tarefa tivesse sido concluída ou cancelada antes da chamada de método, mas uma ou mais tarefas tivessem entrado nesses estados após a chamada de método, o método retornava false.<br />No .NET Framework 4.5, essas sobrecargas de método agora retornarão false se alguma tarefa ainda estiver em execução quando o intervalo de tempo limite expirar, e elas vão gerar uma exceção AggregateException somente se uma tarefa de entrada tiver sido cancelada (não importa se antes ou depois da chamada de método) e nenhuma outra tarefa estiver em execução.|  
|Sugestão|Se uma AggregateException estava sendo capturada como um meio de detectar uma tarefa que foi cancelada antes da chamada WaitAll que está sendo invocada, esse código deverá fazer a mesma detecção por meio da propriedade IsCanceled (por exemplo: .Any(t => t.IsCanceled)), uma vez que o .NET 4.6 vai juntar esse caso apenas se todas as tarefas esperadas forem concluídas antes do tempo limite.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.Int32%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.WaitAll%28System.Threading.Tasks.Task%5B%5D%2CSystem.TimeSpan%29?displayProperty=fullName>|  
|Analisadores|CD0026|  
  
<a name="diagnostic27"></a>   
## <a name="27-change-in-behavior-in-data-definition-language-ddl-apis"></a>27: mudança de comportamento nas APIs DDL (Linguagem de Definição de Dados)  
  
|||  
|-|-|  
|Detalhes|O comportamento dos APIs DDL quando AttachDBFilename é especificado foi alterado da seguinte forma:<br /><br /> As cadeias de conexão não precisam especificar um valor de Catálogo Inicial. Anteriormente, AttatchDBFilename e Catálogo Inicial eram obrigatórios.<br /><br /> Se AttatchDBFilename e Catálogo Inicial forem especificados e o arquivo MDF fornecido existir, o método ObjectContext.DatabaseExists retornará true. Antigamente, ele retornava false.<br /><br /> Se AttatchDBFilename e Catálogo Inicial forem especificados e o arquivo MDF fornecido existir, chamar o método ObjectContext.DeleteDatabase excluirá os arquivos.<br /><br /> Se ObjectContext.DeleteDatabase for chamado quando a cadeia de conexão especificar um valor AttachDBFilename com um MDF e um Catálogo Inicial que não existem, o método vai gerar uma exceção InvalidOperationException. Antigamente, ele gerava uma exceção SqlException.|  
|Sugestão|Essas alterações facilitam a criação de ferramentas e aplicativos que usam APIs de DDL. Essas alterações podem afetar a compatibilidade do aplicativo nas seguintes situações:<br /><br /> O usuário escreve um código que executa um comando DROP DATABASE diretamente, em vez de chamar ObjectContext.DeleteDatabase se ObjectContext.DatabaseExists retornar true. Isso quebrará o código existente se o banco de dados não estiver anexado, mas um arquivo MDF existir.<br /><br /> O usuário escreve um código que espera que o método ObjectContext.DeleteDatabase gere uma exceção SqlException, em vez de uma exceção InvalidOperationException quando o Catálogo Inicial e o arquivo MDF não existirem.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0027|  
  
<a name="diagnostic28"></a>   
## <a name="28-machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>28: Os métodos MachineKey.Encode e MachineKey.Decode agora estão obsoletos  
  
|||  
|-|-|  
|Detalhes|Esses métodos são agora obsoletos. A compilação de código que chama estes métodos gera um aviso do compilador.|  
|Sugestão|As alternativas recomendadas são [MachineKey.Protect](https://msdn.microsoft.com/library/system.web.security.machinekey.protect\(v=vs.110\).aspx) e [MachineKey.Unprotect](https://msdn.microsoft.com/library/system.web.security.machinekey.unprotect\(v=vs.110\).aspx). Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo. Ainda há suporte para as APIs.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Web.Security.MachineKey.Decode%28System.String%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName><br /><br /> <xref:System.Web.Security.MachineKey.Encode%28System.Byte%5B%5D%2CSystem.Web.Security.MachineKeyProtection%29?displayProperty=fullName>|  
|Analisadores|CD0028|  
  
<a name="diagnostic29"></a>   
## <a name="29-the-replace-method-in-odata-urls-is-disabled-by-default"></a>29: O método Replace nas URLs do OData é desabilitado por padrão  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5, o método Replace em URLs do OData é desabilitado por padrão. Quando o Replace do OData está desabilitado (agora por padrão), qualquer solicitação de usuário, incluindo funções de substituição (que são incomuns), falha.|  
|Sugestão|Se o método de substituição for necessário (o que é incomum), ele poderá ser reabilitado por meio das [definições de configuração](https://msdn.microsoft.com/library/system.data.services.configuration.dataservicesfeaturessection.replacefunction.aspx). No entanto, um método de substituição habilitado pode dar abertura para vulnerabilidades de segurança, devendo ser usado somente depois de análise cuidadosa.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Data.Services.DataService%601?displayProperty=fullName>|  
|Analisadores|CD0029|  
  
<a name="diagnostic30"></a>   
## <a name="30-systemservicemodelwebwebservicehost-object-no-longer-adds-a-default-endpoint"></a>30: O objeto System.ServiceModel.Web.WebServiceHost não adiciona mais um ponto de extremidade padrão  
  
|||  
|-|-|  
|Detalhes|O objeto System.ServiceModel.Web.WebServiceHost não adiciona mais um ponto de extremidade padrão se um ponto de extremidade explícito tiver sido adicionado pelo código do aplicativo.|  
|Sugestão|Se os usuários forem esperar para poderem se conectar a um ponto de extremidade padrão e outros pontos de extremidade explícitos forem adicionados ao WebServiceHost, os pontos de extremidade padrão também deverão ser explicitamente adicionados (usando AddDefaultEndpoints).|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.ServiceModel.Description.ServiceEndpoint%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%29?displayProperty=fullName><br /><br /> <xref:System.ServiceModel.ServiceHostBase.AddServiceEndpoint%28System.String%2CSystem.ServiceModel.Channels.Binding%2CSystem.Uri%2CSystem.Uri%29?displayProperty=fullName>|  
|Analisadores|CD0030A<br /><br /> CD0030B|  
  
<a name="diagnostic31"></a>   
## <a name="31-eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>31: EventSource.WriteEvent deve passar a WriteEvent os mesmos parâmetros que recebeu (mais ID)  
  
|||  
|-|-|  
|Detalhes|O tempo de execução agora impõe o contrato que especifica o seguinte: uma classe derivada de EventSource que define um método de evento ETW deve chamar o método de classe base EventSource.WriteEvent com a ID do evento seguido dos mesmos argumentos que o método de evento ETW passou.|  
|Sugestão|Uma exceção IndexOutOfRangeException será gerada se um EventListener ler dados de EventSource no processo de origem do evento que viola esse contrato.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Tempo de execução|  
|Analisadores|CD0031|  
  
<a name="diagnostic32"></a>   
## <a name="32-minfreememorypercentagetoactiveservice-is-now-respected"></a>32: MinFreeMemoryPercentageToActiveService agora é respeitado  
  
|||  
|-|-|  
|Detalhes|Essa configuração estabelece a memória mínima que deve estar disponível no servidor para que um serviço WCF possa ser ativado. Ela foi desenvolvida para impedir exceções OutOfMemoryException. No .NET Framework 4.5, essa configuração não tinha nenhum efeito. No .NET Framework 4.5.1, essa configuração é observada.|  
|Sugestão|Ocorrerá uma exceção se a memória livre disponível no servidor Web for menor que a porcentagem definida pela definição de configuração. Alguns serviços WCF iniciados com êxito e executados em um ambiente de memória restrito agora podem falhar.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Tempo de execução|  
|Analisadores|CD0032|  
  
<a name="diagnostic33"></a>   
## <a name="33-xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>33: A expansão da entidade DTD de XmlTextReader é limitada a 10.000.000 caracteres  
  
|||  
|-|-|  
|Detalhes|A expansão da entidade DTD agora é limitada a 10.000.000 de caracteres. O carregamento de arquivos XML sem expansão de entidade DTD ou com expansão de entidade DTD limitada não é afetado. Arquivos com entidades DTD que se expandem para mais de 10.000.000 caracteres falham ao carregar e geram uma exceção.|  
|Sugestão|Se o limite da expansão da entidade DTD for muito inferior a 10.000.000, o valor poderá ser substituído pela propriedade [XmlReaderSettings.MaxCharactersFromEntities](https://msdn.microsoft.com/library/system.xml.xmlreadersettings.maxcharactersfromentities%28v=vs.110%29.aspx). Um XmlReaderSettings com o valor MaxCharactersFromEntity adequado pode ser passado para [XmlReader.Create](https://msdn.microsoft.com/library/System.Xml.XmlReader.Create\(v=vs.110\).aspx)|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Xml.XmlTextReader.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.Stream%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.Stream%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.IO.TextReader%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.String%2CSystem.Xml.XmlNodeType%2CSystem.Xml.XmlParserContext%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader.%23ctor%28System.Xml.XmlNameTable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.XmlTextReader?displayProperty=fullName>|  
|Analisadores|CD0033|  
  
<a name="diagnostic35"></a>   
## <a name="35-xslt-style-sheet-exception-message-changed"></a>35: Mensagem de exceção da folha de estilo XSLT alterada  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, o texto da mensagem de erro quando um arquivo XSLT é muito complexo é "A folha de estilo é muito complexa". Nas versões anteriores, a mensagem de erro era "Erro de compilação de XSLT." O código do aplicativo que depende do texto da mensagem de erro não funcionará. No entanto, os tipos de exceção permanecem os mesmos, de modo que essa modificação não deve ter um impacto real.|  
|Sugestão|Atualize qualquer código de aplicativo, dependendo da mensagem de exceção dessa condição de erro, para esperar a nova mensagem ou (ainda melhor) atualize o código para depender somente do tipo de exceção ([XsltException](https://msdn.microsoft.com/library/system.xml.xsl.xsltexception\(v=vs.110\).aspx)), que não foi alterado.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Reflection.MethodInfo%2CSystem.Byte%5B%5D%2CSystem.Type%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.String%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XPath.IXPathNavigable%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Xml.XmlReader%2CSystem.Xml.Xsl.XsltSettings%2CSystem.Xml.XmlResolver%29?displayProperty=fullName>|  
|Analisadores|CD0035|  
  
<a name="diagnostic36"></a>   
## <a name="36-wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>36: O WF agora serializa Expressions.Literal\<T> DateTimes de modo diferente (interrompe analisadores XAML personalizados)  
  
|||  
|-|-|  
|Detalhes|O objeto [ValueSerializer](https://msdn.microsoft.com/library/system.windows.markup.valueserializer\(v=vs.110\).aspx) associado converterá um objeto DateTime ou DateTimeOffset, cujos componentes Second e Millisecond são diferentes de zero e (para um valor DateTime) cuja propriedade DateTime.Kind não seja Não especificada, na sintaxe do elemento de propriedade, e não em uma cadeia de caracteres. Essa alteração permite que os valores de DateTime e DateTimeOffset sejam cíclicos. Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.|  
|Sugestão|Essa alteração permite que os valores de DateTime e DateTimeOffset sejam cíclicos. Os analisadores XAML personalizados que assumem que a entrada XAML está na sintaxe de atributo não funcionará corretamente.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0036|  
  
<a name="diagnostic37"></a>   
## <a name="37-new-enum-values-in-wpfs-pagerangeselection"></a>37: Novos valores de enumeração em PageRangeSelection do WPF  
  
|||  
|-|-|  
|Detalhes|Dois novos membros (CurrentPage e SelectedPage) foram adicionados à enumeração [PageRangeSelection](https://msdn.microsoft.com/library/system.windows.controls.pagerangeselection\(v=vs.110\).aspx).|  
|Sugestão|Na maioria das vezes, essas mudanças não afetarão o código do usuário. De qualquer forma, o código que depende de um número específico de elementos existentes nas chamadas Enum.GetNames ou Enum.GetValues no tipo PageRangeSelection deve ser modificado.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>|  
|Analisadores|CD0037|  
  
<a name="diagnostic38"></a>   
## <a name="38-wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>38: DispatcherSynchronizationContext.CreateCopy do WPF agora retorna uma nova cópia em vez da instância atual  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4, DispatcherSynchronizationContext.CreateCopy() retornava uma referência à instância atual, basicamente como uma otimização de desempenho. No .NET Framework 4.5, ele retorna uma nova instância que possibilita, pela primeira vez, concluir que referências iguais indicam que o thread em execução está no contexto de sincronização correto.  É provável que o código que verifica a identidade dessas referências seja afetado, mas, devido à alteração, o código que chama DispatcherSynchronizationContext.CreateCopy deve ser testado como parte da migração para o .NET Framework 4.5 ou mais recente.|  
|Sugestão|Esteja ciente de que DispatcherSynchronizationContext.CreateCopy() agora retornará um novo objeto SynchronizationContext.  Antigamente, o código que usava equivalência de referências gerada dessa maneira não era de fato verificado se estava no contexto apropriado, mas agora o é quando compilado no .NET 4.5 ou mais recente.  Embora não haja probabilidade de causar problemas, praticar os caminhos de código afetados deve ser suficiente para determinar se isso impõe algum problema.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=fullName>|  
|Analisadores|CD0038|  
  
<a name="diagnostic39"></a>   
## <a name="39-systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>39: System.Threading.Tasks.Task não gera mais ObjectDisposedException depois que o objeto é descartado  
  
|||  
|-|-|  
|Detalhes|Exceto para Task.IAsyncResult.AsyncWaitHandle, os métodos System.Threading.Tasks.Task não geram mais uma exceção ObjectDisposedException depois que o objeto é descartado.<br />Essa alteração permite o uso de tarefas em cache. Por exemplo, um método pode retornar uma tarefa em cache para representar uma operação já concluída em vez de alocar uma nova tarefa. Isso era impossível nas versões anteriores do .NET Framework porque qualquer consumidor da tarefa poderia descartá-los, o que a tornava inutilizável.|  
|Sugestão|Lembre-se de que os métodos Task podem não gerar mais ObjectDisposedExceptions nos casos em que o objeto é descartado. Se um aplicativo dependia dessa exceção para saber que uma tarefa foi descartada, ele deverá ser atualizado para verificar explicitamente o status da tarefa usando [Task.Status](https://msdn.microsoft.com/library/system.threading.tasks.task.status\(v=vs.110\).aspx).|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0039|  
  
<a name="diagnostic40"></a>   
## <a name="40-different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a>40: Tratamento de exceção diferente para os métodos ObjectContext.CreateDatabase e DbProviderServices.CreateDatabase  
  
|||  
|-|-|  
|Detalhes|A partir do .NET 4.5, se houver falha na criação do banco de dados, os métodos `CreateDatabase` tentarão remover o banco de dados vazio. Se essa operação for bem-sucedida, a `SQLException` original será propagada (em vez da `InvalidOperationException` que sempre era gerada no .NET 4.0)|  
|Sugestão|Ao capturar uma InvalidOperationException durante a execução de ObjectContext.CreateDatabase ou DbProviderServices.CreateDatabase, SQLExceptions agora também deve ser capturada.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Data.Common.DbProviderServices.CreateDatabase%28System.Data.Common.DbConnection%2CSystem.Nullable%7BSystem.Int32%7D%2CSystem.Data.Metadata.Edm.StoreItemCollection%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analisadores|CD0040|  
  
<a name="diagnostic41"></a>   
## <a name="41-objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>41: ObjectContext.Translate e ObjectContext.ExecuteStoreQuery agora dão suporte ao tipo de enumeração  
  
|||  
|-|-|  
|Detalhes|No .NET 4.0, o parâmetro genérico `T` de `ObjectContext.Translate` e os métodos `ObjectContext.ExecuteStoreQuery` não podiam ser uma enumeração. Agora há suporte para esse cenário.|  
|Sugestão|Se Translate ou ExecuteStoreQuery era chamado em um tipo de enumeração no .NET 4.0, era retornado "0". Se esse comportamento fosse desejável, as chamadas deveriam ser substituídas por uma constante 0 (ou o equivalente de enumeração dele).|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601%28System.String%2CSystem.String%2CSystem.Data.Objects.MergeOption%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%29?displayProperty=fullName><br /><br /> <xref:System.Data.Objects.ObjectContext.Translate%60%601%28System.Data.Common.DbDataReader%2CSystem.String%2CSystem.Data.Objects.MergeOption%29?displayProperty=fullName>|  
|Analisadores|CD0041|  
  
<a name="diagnostic42"></a>   
## <a name="42-enumerableemptytresult-always-returns-cached-instance"></a>42: Enumerable.Empty\<TResult> sempre retorna instância em cache  
  
|||  
|-|-|  
|Detalhes|A partir do .NET 4.5, `Enumerable.Empty` sempre retornará uma instância `IEnumerable<T>` interna em cache.<br /><br /> Antigamente, `Enumerable.Empty` armazenava em cache um `IEnumerable<T>` vazio no momento em que a API era chamada, o que significa que, em algumas condições nas quais `Enumerable.Empty` era chamado de forma rápida e simultânea, diferentes instâncias do tipo poderiam ser retornadas para diferentes chamadas à API.|  
|Sugestão|Como o comportamento anterior não era determinístico, é improvável que o código dependesse dele. No entanto, na improbabilidade de que enumeráveis vazios estivessem sendo comparados e, às vezes, esperados que fosse diferentes, matrizes vazias explícitas deviam ser criadas (`new T[0]`) em vez de usar `Enumerable.Empty`.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=fullName>|  
|Analisadores|CD0042|  
  
<a name="diagnostic43"></a>   
## <a name="43-httprequestcontentencoding-property-prohibits-utf7"></a>43: A propriedade HttpRequest.ContentEncoding proíbe a UTF7  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5, a codificação UTF-7 está proibida nos corpos de HttpRequests. Os dados para aplicativos que dependem de dados de entrada UTF-7 não serão decodificados corretamente em alguns casos.|  
|Sugestão|De modo ideal, os aplicativos devem ser atualizado para não usar a codificação UTF-7 em HttpRequests. De modo alternativo, o comportamento herdado pode ser restaurado usando o atributo `aspnet:AllowUtf7RequestContentEncoding` do elemento [appSettings](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx).|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=fullName>|  
|Analisadores|CD0043|  
  
<a name="diagnostic44"></a>   
## <a name="44-httputilityjavascriptstringencode-escapes-ampersand"></a>44: HttpUtility.JavaScriptStringEncode escapa o E comercial  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5, JavaScriptStringEncode escapa o caractere E comercial (&).|  
|Sugestão|Se seu aplicativo depende do comportamento anterior desse método, você poderá adicionar uma definição aspnet:JavaScriptDoNotEncodeAmpersand ao [elemento appSettings do ASP.NET](https://msdn.microsoft.com/library/hh975440\(v=vs.110\).aspx) no seu arquivo de configuração.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.HttpUtility.JavaScriptStringEncode%28System.String%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analisadores|CD0044A<br /><br /> CD0044B|  
  
<a name="diagnostic46"></a>   
## <a name="46-eventlistener-truncates-strings-with-embedded-nulls"></a>46: EventListener trunca cadeias de caracteres com nulos inseridos  
  
|||  
|-|-|  
|Detalhes|EventListener trunca cadeias de caracteres com nulos inseridos. Os caracteres nulos não são compatíveis com a classe EventSource. A alteração afeta apenas os aplicativos que usam EventListener para ler dados EventSource no processo e que usam caracteres nulos como delimitadores.|  
|Sugestão|Os dados EventSource devem ser atualizados, se possível, para não usar caracteres nulos inseridos.|  
|Escopo|Edge|  
|Versão|4.5.1|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Diagnostics.Tracing.EventListener.%23ctor?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%2CSystem.Diagnostics.Tracing.EventKeywords%2CSystem.Collections.Generic.IDictionary%7BSystem.String%2CSystem.String%7D%29?displayProperty=fullName>|  
|Analisadores|CD0046|  
  
<a name="diagnostic48"></a>   
## <a name="48-obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>48: ObsoleteAttribute exporta ObsoleteAttribute e DeprecatedAttribute em cenários WinMD  
  
|||  
|-|-|  
|Detalhes|Quando você cria uma biblioteca de Metadados do Windows (arquivo .winmd), o atributo ObsoleteAttribute é exportado como ObsoleteAttribute e Windows.Foundation.DeprecatedAttribute.|  
|Sugestão|A recompilação do código-fonte existente que usa o atributo ObsoleteAttribute pode gerar avisos durante o consumo desse código no C++/CX ou JavaScript.<br /><br /> Não é aconselhável a aplicação de ObsoleteAttribute e Windows.Foundation.DeprecatedAttribute para codificar em assemblies gerenciados; isso pode resultar em avisos de compilação.|  
|Escopo|Edge|  
|Versão|4.5.1|  
|Tipo|Redirecionando|  
|Analisadores|CD0048A<br /><br /> CD0048B|  
  
<a name="diagnostic49"></a>   
## <a name="49-resolveassemblyreference-task-now-warns-on-dependencies-with-the-wrong-architecture"></a>49: A tarefa ResolveAssemblyReference agora avisa sobre dependências com arquitetura incorreta  
  
|||  
|-|-|  
|Detalhes|A tarefa emite um aviso, MSB3270, que indica que uma referência ou qualquer uma de suas dependências não corresponde à arquitetura do aplicativo. Por exemplo, isso ocorrerá se um aplicativo que tenha sido compilado com a opção anycpu incluir uma referência x86. Esse cenário pode resultar em uma falha do aplicativo no tempo de execução (nesse caso, se o aplicativo for implantado como um processo x64).|  
|Sugestão|Há duas áreas de impacto:<br /><br /> A recompilação gerencia os avisos que não foram exibidos quando o aplicativo foi compilado com uma versão anterior do MSBuild. Entretanto, como o aviso identifica uma possível fonte de falha no tempo de execução, ele deve ser investigado e resolvido.<br /><br /> Se os avisos forem tratados como erros, o aplicativo não será compilado.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Redirecionando|  
|Analisadores|CD0049|  
  
<a name="diagnostic51"></a>   
## <a name="51-wpf-textbox-defaults-to-undo-limit-of-100"></a>51: o padrão da Caixa de Texto do WPF é o limite de 100 na ação desfazer  
  
|||  
|-|-|  
|Detalhes|No .NET 4.5, o limite padrão da ação desfazer para uma caixa de texto do WPF é 100 (ao contrário de ser ilimitado como no .NET 4.0)|  
|Sugestão|Se um limite de 100 da ação desfazer for muito baixo, o limite poderá ser definido explicitamente com a propriedade UndoLimit da Caixa de Texto|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Controls.TextBox?displayProperty=fullName>|  
|Analisadores|CD0051|  
  
<a name="diagnostic55"></a>   
## <a name="55-exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>55: Exceções durante o processamento não observado em System.Threading.Tasks.Task não são mais propagadas no thread do finalizador  
  
|||  
|-|-|  
|Detalhes|Como a classe System.Threading.Tasks.Task representa uma operação assíncrona, ela captura todas as exceções não graves que ocorrem durante o processamento assíncrono. No .NET Framework 4.5, se uma exceção não for observada e seu código nunca aguarda a tarefa, a exceção não será mais propagada no thread do finalizador e causará a falha do processo durante a coleta de lixo. Essa alteração melhora a confiabilidade de aplicativos que usam a classe Task para executar processamento assíncrono não observado.|  
|Sugestão|Se um aplicativo depender de exceções assíncronas não observadas que se propagam para o thread do finalizador, o comportamento anterior poderá ser restaurado com o fornecimento de um manipulador apropriado para o evento [TaskScheduler.UnobservedTaskException](https://msdn.microsoft.com/library/system.threading.tasks.taskscheduler.unobservedtaskexception\(v=vs.110\).aspx) ou com a definição de um [elemento de configuração de tempo de execução](https://msdn.microsoft.com/library/jj160346%28v=vs.110%29.aspx).|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Action%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7BSystem.Threading.Tasks.Task%7B%60%600%7D%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Run%60%601%28System.Func%7B%60%600%7D%2CSystem.Threading.CancellationToken%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.Task.Start%28System.Threading.Tasks.TaskScheduler%29?displayProperty=fullName>|  
|Analisadores|CD0055|  
  
<a name="diagnostic58"></a>   
## <a name="58-iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a>58: A propriedade IAsyncResult.CompletedSynchronously deve estar correta para a tarefa resultante a ser concluída  
  
|||  
|-|-|  
|Detalhes|Ao chamar TaskFactory.FromAsync, a implementação da propriedade IAsyncResult.CompletedSynchronously deve estar correta para a tarefa resultante a ser concluída. Isto é, a propriedade deverá retornar true se, e apenas se, a implementação for concluída de modo síncrono. Anteriormente, a propriedade não era verificada.|  
|Sugestão|Se as implementações de IAsyncResult retornarem true corretamente para a propriedade CompletedSynchronusly somente quando uma tarefa for concluída de modo síncrono, nenhuma interrupção será observada. Os usuários devem revisar as implementações de IAsyncResult que possuem (se houver) para garantir que eles sejam avaliadas corretamente se uma tarefa for concluída de modo síncrono ou não.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%28System.IAsyncResult%2CSystem.Action%7BSystem.IAsyncResult%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7BSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601%28System.IAsyncResult%2CSystem.Func%7BSystem.IAsyncResult%2C%60%600%7D%2CSystem.Threading.Tasks.TaskCreationOptions%2CSystem.Threading.Tasks.TaskScheduler%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%601%7D%2C%60%600%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%602%7D%2C%60%600%2C%60%601%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Action%7BSystem.IAsyncResult%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%29?displayProperty=fullName><br /><br /> <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604%28System.Func%7B%60%600%2C%60%601%2C%60%602%2CSystem.AsyncCallback%2CSystem.Object%2CSystem.IAsyncResult%7D%2CSystem.Func%7BSystem.IAsyncResult%2C%60%603%7D%2C%60%600%2C%60%601%2C%60%602%2CSystem.Object%2CSystem.Threading.Tasks.TaskCreationOptions%29?displayProperty=fullName>|  
|Analisadores|CD0058|  
  
<a name="diagnostic59"></a>   
## <a name="59-log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>59: O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server  
  
|||  
|-|-|  
|Detalhes|Quando o método CreateDatabase é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename). Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.|  
|Sugestão|Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>|  
|Analisadores|CD0059|  
  
<a name="diagnostic60"></a>   
## <a name="60-pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a>60: O evento Page.LoadComplete não faz mais com que o controle System.Web.UI.WebControls.EntityDataSource invoque a associação de dados  
  
|||  
|-|-|  
|Detalhes|O evento `Page.LoadComplete` não faz mais com que o controle System.Web.UI.WebControls.EntityDataSource invoque a associação de dados para fazer alterações nos parâmetros create/update/delete. Essa alteração elimina um percurso irrelevante para o banco de dados, impede que os valores dos controles sejam redefinidos e gera um comportamento consistente com outros controles de dados, como SqlDataSource e ObjectDataSource. Essa alteração gera um comportamento diferente em um evento improvável no qual os aplicativos dependam da associação de dados no evento `Page.LoadComplete`.|  
|Sugestão|Se houver necessidade de vinculação de dados, invoque manualmente a associação de dados em um evento que seja anterior no post-back.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0060|  
  
<a name="diagnostic61"></a>   
## <a name="61-webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a>61: WebUtility.HtmlDecode não decodifica mais sequências de entrada inválidas  
  
|||  
|-|-|  
|Detalhes|Por padrão, os métodos de decodificação não decodificam mais uma sequência de entrada válida em uma cadeia de caracteres UTF-16 inválida. Em vez disso, eles retornam a entrada original.|  
|Sugestão|A alteração na saída do decodificador deve importar somente se você armazenar dados binários em vez de dados UTF-16 em cadeias de caracteres. Para controlar explicitamente esse comportamento, defina o atributo `aspnet:AllowRelaxedUnicodeDecoding` do elemento [appSettings](https://msdn.microsoft.com/library/ms228154\(v=vs.110\).aspx) como true para habilitar o comportamento herdado ou como false para habilitar o comportamento atual.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Net.WebUtility.HtmlDecode%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.HtmlDecode%28System.String%2CSystem.IO.TextWriter%29?displayProperty=fullName><br /><br /> <xref:System.Net.WebUtility.UrlDecode%28System.String%29?displayProperty=fullName>|  
|Analisadores|CD0061|  
  
<a name="diagnostic63"></a>   
## <a name="63-apps-published-with-clickonce-that-use-a-sha-256-code-signing-certificate-may-fail-on-windows-2003"></a>63: Os aplicativos publicados com ClickOnce que usam um certificado de autenticação de código SHA-256 podem falhar no Windows 2003  
  
|||  
|-|-|  
|Detalhes|O executável é assinado com SHA256. Antes, ele era assinado com SHA1, independentemente se o certificado de assinatura de código era SHA-1 ou SHA-256. Isso se aplica a:<br /><br /> Todos os aplicativos compilados com o Visual Studio 2012 ou posterior.<br /><br /> Os aplicativos compilados com o Visual Studio 2010 ou anteriores em sistemas com o .NET Framework 4.5.<br /><br /> Além disso, se o .NET Framework 4.5 ou posterior estiver presente, o manifesto do ClickOnce também será assinado com certificados SHA-256 para SHA-256, independentemente da versão do .NET Framework na qual ele foi compilado.|  
|Sugestão|A mudança na assinatura do executável do ClickOnce afeta apenas os sistemas Windows Server 2003; eles exigem a instalação do KB 938397.<br /><br /> A alteração na assinatura do manifesto com SHA-256, mesmo quando um aplicativo destina-se ao .NET Framework 4.0 ou versões anteriores, introduz uma dependência de tempo de execução no .NET Framework 4.5 ou uma versão posterior.|  
|Escopo|Edge|  
|Versão|4.5-4.6|  
|Tipo|Redirecionando|  
|Analisadores|CD0063|  
  
<a name="diagnostic68"></a>   
## <a name="68-dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>68: DbParameter.Precision e DbParameter.Scale agora são membros virtuais públicos  
  
|||  
|-|-|  
|Detalhes|DbParameter.Precision e DbParameter.Scale são implementados como propriedades virtuais públicas. Eles substituem a implementação explícita de interface correspondente, DbParameter.IDbDataParameter.Precision e DbParameter.IDbDataParameter.Scale.|  
|Sugestão|Ao recompilar um provedor de banco de dados ADO.NET, essas diferenças exigirão que a palavra-chave "override" seja aplicada às propriedades Precision e Scale. Isso é necessário somente na recompilação dos componentes; binários existentes continuarão funcionando.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Data.Common.DbParameter.Precision?displayProperty=fullName><br /><br /> <xref:System.Data.Common.DbParameter.Scale?displayProperty=fullName>|  
|Analisadores|CD0068|  
  
<a name="diagnostic73"></a>   
## <a name="73-dataobjectgetdata-now-retrieves-data-as-utf-8"></a>73: DataObject.GetData agora recupera dados como UTF-8  
  
|||  
|-|-|  
|Detalhes|Para aplicativos direcionados ao .NET Framework 4 ou que são executados no .NET Framework 4.5.1 ou versões anteriores, o DataObject.GetData recupera dados formatados em HTML como uma cadeia de caracteres ASCII. Como resultado, caracteres não ASCII (caracteres cujos códigos ASCII são maiores que 0x7F) são representados por dois caracteres aleatórios.<br /><br /> Para aplicativos direcionados ao .NET Framework 4.5 ou posteriores e executados no .NET Framework 4.5.2, o `DataObject.GetData` recupera dados formatados em HTML como UTF-8, que representam caracteres maiores que 0x7F corretamente.|  
|Sugestão|Se você implementou uma solução alternativa para o problema de codificação com cadeias de caracteres formatadas em HTML (por exemplo, codificando explicitamente a cadeia de caracteres HTML recuperadas da Área de Transferência e enviando-a para o método UTF8Encoding.GetString) e está redirecionando seu aplicativo da versão 4 para a versão 4.5, essa solução deverá ser removida.<br /><br /> Se o comportamento antigo for necessário por algum motivo, o aplicativo poderá ser direcionado ao .NET Framework 4.0 para obter esse comportamento.|  
|Escopo|Edge|  
|Versão|4.5.2|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Windows.DataObject.GetData%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.String%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Windows.DataObject.GetData%28System.Type%29?displayProperty=fullName>|  
|Analisadores|CD0073|  
  
<a name="diagnostic75"></a>   
## <a name="75-targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>75: TargetFrameworkName para o domínio de aplicativo padrão não será mais padronizado para nulo se não for definido  
  
|||  
|-|-|  
|Detalhes|O TargetFrameworkName era nulo anteriormente no domínio de aplicativo padrão, a menos que fosse explicitamente definido. A partir da 4.6, a propriedade TargetFrameworkName para o domínio de aplicativo padrão terá um valor padrão derivado do TargetFrameworkAttribute (se um estiver presente). Os domínios de aplicativo não padrão continuarão herdando o respectivo TargetFrameworkName do domínio de aplicativo padrão (que não será padronizado para nulo na 4.6), a menos que sejam explicitamente substituídos.|  
|Sugestão|O código deve ser atualizado para não depender do `AppDomainSetup.TargetFrameworkName` que padroniza para nulo. Se for necessário que essa propriedade continue sendo avaliada como nula, ela poderá ser explicitamente definida para esse valor.|  
|Escopo|Edge|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>|  
|Analisadores|CD0075B<br /><br /> CD0075A|  
  
<a name="diagnostic76"></a>   
## <a name="76-x509certificate2tostringbool-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>76: X509Certificate2.ToString(bool) agora não é gerado quando o .NET não pode tratar o certificado  
  
|||  
|-|-|  
|Detalhes|Anteriormente, esse método seria lançado se "true" fosse passado para o parâmetro verbose e se houvesse certificados instalados que não tivessem suporte do .NET Framework. Agora, o método será bem-sucedido e retornará uma cadeia de caracteres válida que omita as partes inacessíveis do certificado.|  
|Sugestão|Qualquer código dependente do X509Certificate2.ToString(bool) deve ser atualizado para esperar que a cadeia de caracteres retornada possa excluir alguns dados do certificado (como chave pública, chave privada e extensões) em alguns casos nos quais a API teria sido gerada anteriormente.|  
|Escopo|Edge|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString%28System.Boolean%29?displayProperty=fullName>|  
|Analisadores|CD0076|  
  
<a name="diagnostic77"></a>   
## <a name="77-reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>77: Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo  
  
|||  
|-|-|  
|Detalhes|Os objetos Reflection não podem mais ser passados de código gerenciado para clientes DCOM fora do processo. Os seguintes tipos são afetados:<br /><br /> Assembly<br /><br /> MemberInfo (e seus tipos derivados, incluindo FieldInfo, MethodInfo, Type e TypeInfo)<br /><br /> MethodBody<br /><br /> Módulo<br /><br /> ParameterInfo.<br /><br /> Chamadas a `IMarshal` para o retorno do objeto `E_NOINTERFACE`.|  
|Sugestão|Atualize o código de marshaling para trabalhar com objetos de não reflexão|  
|Escopo|Secundário|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|Analisadores|CD0077|  
  
<a name="diagnostic78"></a>   
## <a name="78-contentdisposition-datetimes-returns-slightly-different-string"></a>78: ContentDisposition DateTimes retorna cadeia de caracteres ligeiramente diferente  
  
|||  
|-|-|  
|Detalhes|As representações de cadeia de caracteres de ContentDispositions foram atualizadas, a partir da versão 4.6, para sempre representarem o componente de hora de um DateTime com dois dígitos. Isso está em conformidade com a [RFC822](http://www.ietf.org/rfc/rfc0822.txt) e [RFC2822](http://www.ietf.org/rfc/rfc2822.txt). Isso faz com que `ContentDisposition.ToString` retorne uma cadeia de caracteres ligeiramente diferente na versão 4.6 em cenários em que um dos elementos de tempo da disposição era anterior a 10:00 AM. Observe que ContentDispositions, às vezes, são serializados por meio de conversão em cadeias de caracteres, de modo que qualquer operação ToString de ContentDisposition ou chamadas GetHashCode devem ser revisadas.|  
|Sugestão|Não espere que essas representações de cadeia de caracteres de ContentDispositions de diferentes versões do .NET Framework sejam corretamente comparadas umas com as outras. Converta as cadeias de caracteres de volta em ContentDispositions, se possível, antes de realizar uma comparação.|  
|Escopo|Secundário|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=fullName><br /><br /> <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=fullName>|  
|Analisadores|CD0078|  
  
<a name="diagnostic82"></a>   
## <a name="82-workflowdesignerload-doesnt-remove-symbol-property"></a>82: WorkflowDesigner.Load não remove a propriedade de símbolo  
  
|||  
|-|-|  
|Detalhes|Ao direcionar o .NET Framework 4.5 no designer de fluxo de trabalho e carregar um fluxo de trabalho 3.5 hospedado novamente com o método WorkflowDesigner.Load(), uma XamlDuplicateMemberException é gerada durante o salvamento do fluxo de trabalho.|  
|Sugestão|Esse bug se manifesta somente no direcionamento do .NET Framework 4.5 no designer de fluxo de trabalho, de modo que a solução alternativa é definir o `WorkflowDesigner.Context.Services.GetService<DesignerConfigurationService>().TargetFrameworkName` para o .NET Framework 4.0.<br /><br /> Como alternativa, o problema pode ser evitado usando o método [WorkflowContext.Load(string)](https://msdn.microsoft.com/library/ee425926\(v=vs.110\).aspx) para carregar o fluxo de trabalho, em vez de [WorkflowDesigner.Load()](https://msdn.microsoft.com/library/ee403482\(v=vs.110\).aspx).|  
|Escopo|Principal|  
|Versão|4.5-4.5.2|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=fullName>|  
|Analisadores|CD0082|  
  
<a name="diagnostic83"></a>   
## <a name="83-sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>83: SqlConnection.Open falha no Windows 7 com BSP ou LSP Winsock não IFS presente  
  
|||  
|-|-|  
|Detalhes|SqlConneciton.Open e OpenAsync falharão no .NET Framework 4.5 se estiverem em execução em um computador com Windows 7 com um BSP ou LSP Winsock não IFS presente no computador.<br /><br /> Para determinar se um BSP ou LSP não IFS está instalado, use o comando `netsh WinSock Show Catalog` e examine cada item `Winsock Catalog Provider Entry` que é retornado. Se o valor de Sinalizadores de Serviço tiver o bit `0x20000` definido, o provedor usará os identificadores do IFS e funcionará corretamente. Se o bit `0x20000` estiver limpo (não definido), trata-se de um BSP ou LSP não IFS.|  
|Sugestão|Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework. Como alternativa, ele pode ser evitado com a remoção de qualquer LSP Winsock não IFS instalado.|  
|Escopo|Secundário|  
|Versão|4.5-4.5.2|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=fullName><br /><br /> <xref:System.Data.SqlClient.SqlConnection.OpenAsync%28System.Threading.CancellationToken%29?displayProperty=fullName>|  
|Analisadores|CD0083|  
  
<a name="diagnostic84"></a>   
## <a name="84-icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>84: O comportamento do evento ICommand.CanExecuteChanged foi alterado no .NET 4.5  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, um CanExecuteChangedEvent era ignorado, a menos que o remetente do evento fosse o mesmo objeto que o objeto que acionou o evento. Esse bug foi corrigido nas atualizações de serviço do .NET Framework 4.5.|  
|Sugestão|Esse bug foi corrigido nas versões de serviço do .NET Framework 4.5, de modo que ele pode ser evitado garantindo que o .NET Framework seja atualizado ou fazendo upgrade para o .NET Framework 4.5.1. Como alternativa, o código do aplicativo que usa ICommand pode ser modificado para garantir que o remetente, ao acionar um comando CanExecuteChanged, seja o mesmo que o objeto que aciona o evento.|  
|Escopo|Secundário|  
|Versão|4.5-4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=fullName>|  
|Analisadores|CD0084|  
  
<a name="diagnostic85"></a>   
## <a name="85-some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>85: Algumas APIs .NET causam EntryPointNotFoundExceptions de primeira chance  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, um pequeno número de métodos .NET começou a gerar EntryPointNotFoundExceptions de primeira chance. Essas exceções eram tratadas dentro do .NET Framework, mas poderiam interromper a automação de teste que não esperava as exceções de primeira chance. Essas mesmas APIs interrompem alguns cenários ApiVerifier quando HighVersionLie é habilitado.|  
|Sugestão|Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1. Como alternativa, a automação de teste pode ser atualizada para não interromper EntryPointNotFoundExceptions de primeira chance.|  
|Escopo|Edge|  
|Versão|4.5-4.5.1|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Diagnostics.Debug.Assert%28System.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%29?displayProperty=fullName><br /><br /> <xref:System.Diagnostics.Debug.Assert%28System.Boolean%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=fullName><br /><br /> <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%29?displayProperty=fullName>|  
|Analisadores|CD0085|  
  
<a name="diagnostic86"></a>   
## <a name="86-scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a>86: Rolar em uma TreeView ou ListBox agrupada no WPF em um VirtualizingStackPanel pode causar travamento  
  
|||  
|-|-|  
|Detalhes|No .NET Framework v4.5, rolar em uma TreeView do WPF em um painel de pilha virtualizado poderá causar travamentos se houver margens no visor (entre os itens na TreeView, por exemplo, ou em um elemento ItemsPresenter). Além disso, em alguns casos, itens de tamanhos diferentes no modo de exibição podem causar instabilidade, mesmo se não houver margens.|  
|Sugestão|Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1. Como alternativa, as margens poderão ser removidas das coleções de exibições (como TreeViews) em painéis de pilha virtualizados se todos os itens contidos forem do mesmo tamanho.|  
|Escopo|Principal|  
|Versão|4.5-4.5.1|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Controls.VirtualizingPanel.SetIsVirtualizing%28System.Windows.DependencyObject%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analisadores|CD0086<br /><br /> CD0086|  
  
<a name="diagnostic89"></a>   
## <a name="89-typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>89: Type.IsAssignableFrom retorna o resultado incorreto para variáveis genéricas com restrições  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, Type.IsAssignableFrom retornará `false` incorretamente em todos os casos para alguns tipos genéricos com restrições.|  
|Sugestão|Esse problema foi corrigido em uma atualização de serviço. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema. Como alternativa, evite usar IsAssignableFrom com tipos genéricos que tenham restrições em parâmetros genéricos. As APIs de reflexão podem ser usadas como uma solução alternativa.|  
|Escopo|Secundário|  
|Versão|4.5-4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Type.IsAssignableFrom%28System.Type%29?displayProperty=fullName>|  
|Analisadores|CD0089<br /><br /> CD0089|  
  
<a name="diagnostic91"></a>   
## <a name="91-entityframework-60-loads-very-slowly-in-apps-launched-from-visual-studio"></a>91: O EntityFramework 6.0 carrega muito lentamente em aplicativos inicializados pelo Visual Studio  
  
|||  
|-|-|  
|Detalhes|A inicialização de um aplicativo no Visual Studio 2013 que usa o EntityFramework 6.0 pode ser muito lenta.|  
|Sugestão|Esse problema foi corrigido no EntityFramework 6.0.2. Atualize o EntityFramework para evitar o problema de desempenho.|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0091|  
  
<a name="diagnostic92"></a>   
## <a name="92-multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>92: O espaçamento de TextBox do ASP.Net de várias linhas é alterado quando se usa AntiXSSEncoder  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.0, linhas extras eram inseridas entre as linhas de uma caixa de texto de várias linhas no postback, se usando o `AntiXSSEncoder`. No .NET Framework 4.5, essas quebras de linhas extras não são incluídas. mas somente se o aplicativo Web for direcionado ao .NET 4.5|  
|Sugestão|Lembre-se de que os aplicativos Web 4.0 redirecionados ao .NET 4.5 podem ter caixas de texto de várias linhas aprimoradas para não inserirem mais quebras de linhas extras. Se isso não for desejável, o aplicativo poderá ter o comportamento antigo durante a execução no .NET Framework 4.5 visando o .NET Framework 4.0.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|Analisadores|CD0092|  
  
<a name="diagnostic95"></a>   
## <a name="95-concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>95: ConcurrentQueue\<T>.TryPeek pode retornar um nulo errado por meio de seus parâmetros de saída  
  
|||  
|-|-|  
|Detalhes|Em alguns cenários multithread, `ConcurentQueue<T>.TryPeek` pode retornar true, mas popular o parâmetro de saída com um valor nulo (em vez do valor correto, inspecionado).|  
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.1. O upgrade para esse Framework resolverá o problema.|  
|Escopo|Principal|  
|Versão|4.5-4.5.1|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek%28%600%40%29?displayProperty=fullName>|  
|Analisadores|CD0095|  
  
<a name="diagnostic98"></a>   
## <a name="98-multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>98: Vários itens em uma única célula TableLayoutPanel podem ser reorganizados  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, se vários itens forem colocados na mesma célula TableLayoutPanel, eles poderão ser exibidos em uma ordem diferente da que eram exibidos no .NET Framework 4.0.|  
|Sugestão|Esse comportamento foi revertido em uma atualização de serviço para o .NET Framework 4.5. Atualize o .NET Framework 4.5 ou faça upgrade para o .NET Framework 4.5.1 ou posterior para corrigir esse problema. Como alternativa, evite o caso ambíguo de vários itens na mesma célula TableLayourPanel.|  
|Escopo|Secundário|  
|Versão|4.5-4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Forms.TableLayoutControlCollection.Add%28System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>|  
|Analisadores|CD0098|  
  
<a name="diagnostic100"></a>   
## <a name="100-foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>100: a variável do iterador Foreach agora tem escopo na iteração, de modo que as semânticas de captura de fechamento são diferentes (no C#5)  
  
|||  
|-|-|  
|Detalhes|A partir do C# 5 (Visual Studio 2012), as variáveis do iterador foreach têm escopo dentro da iteração. Isso poderá causar interrupções se o código anteriormente dependia das variáveis para não ser incluído no fechamento de foreach. O sintoma dessa alteração será que uma variável do iterador passada a um representante será tratada com o valor que ela tinha no momento em que o representante foi criado, e não com o valor que ela tinha no momento em que o representante foi invocado.|  
|Sugestão|De maneira ideal, o código deve ser atualizado para esperar o novo comportamento do compilador. Se as semânticas antigas forem necessárias, a variável do iterador poderá ser substituída por uma variável separada que seja explicitamente colocada fora do escopo do loop.|  
|Escopo|Principal|  
|Versão|4.5|  
|Tipo|Redirecionando|  
|Analisadores|CD0100|  
  
<a name="diagnostic101"></a>   
## <a name="101-htmltextwriter-does-not-render-br-element-correctly"></a>101: HtmlTextWriter não renderiza o elemento \`<br/\>` corretamente  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.6, chamar `HtmlTextWriter.RenderBeginTag()` e `HtmlTextWriter.RenderEndTag()` com um elemento `<BR />` vai inserir corretamente apenas um `<BR />` (em vez de dois)|  
|Sugestão|Se um aplicativo depender da marca `<BR />` extra, `HtmlTextWriter.RenderBeginTag()` deverá ser chamado uma segunda vez. Observe que essa alteração de comportamento afeta apenas aplicativos que são direcionados ao .NET Framework 4.6, de modo que outra opção é direcionar a uma versão anterior do .NET Framework a fim de obter o comportamento antigo.|  
|Escopo|Edge|  
|Versão|4.6|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.String%29?displayProperty=fullName><br /><br /> <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|  
|Analisadores|CD0101|  
  
<a name="diagnostic104"></a>   
## <a name="104-calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a>104: Chamar Items.Refresh em uma ListBox, ListView ou DataGrid do WPF com itens selecionados pode exibir itens duplicados no elemento  
  
|||  
|-|-|  
|Detalhes|No .NET Framework 4.5, chamar ListBox.Items.Refresh do código enquanto itens estiverem selecionados em uma ListBox pode fazer com que os itens selecionados sejam duplicados na lista. Um problema semelhante ocorre com ListView e DataGrid. Isso foi corrigido no .NET Framework 4.6.|  
|Sugestão|Esse problema pode ser contornado de forma programática cancelando a seleção dos itens antes de chamar Refresh e selecionando-os novamente após a conclusão da chamada. Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|  
|Escopo|Secundário|  
|Versão|4.5-4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName>|  
|Analisadores|CD0104|  
  
<a name="diagnostic105"></a>   
## <a name="105-etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>105: EventListeners do ETW não capturam eventos dos provedores com palavras-chave explícitas (como o provedor TPL)  
  
|||  
|-|-|  
|Detalhes|EventListeners do ETW com uma máscara de palavra-chave em branco não capturam eventos corretamente dos provedores com palavras-chave explícitas. No .NET Framework 4.5, o provedor TPL começou a fornecer palavras-chave explícitas e disparou esse problema. No .NET Framework 4.6, EventListeners foram atualizados para não apresentarem mais esse problema.|  
|Sugestão|Para contornar esse problema, substitua as chamadas a EnableEvents(eventSource, level) por chamadas à sobrecarga de EnableEvents, que especifica explicitamente a máscara "qualquer palavra-chave" a ser usada: `EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))`.<br /><br /> Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.|  
|Escopo|Edge|  
|Versão|4.5-4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%28System.Diagnostics.Tracing.EventSource%2CSystem.Diagnostics.Tracing.EventLevel%29?displayProperty=fullName>|  
|Analisadores|CD0105|  
  
<a name="diagnostic109"></a>   
## <a name="109-building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a>109: A compilação de um edmx do Entity Framework com o Visual Studio 2013 pode falhar com o erro MSB4062 se estiver usando as tarefas EntityDeploySplit ou EntityClean  
  
|||  
|-|-|  
|Detalhes|As ferramentas do MSBuild 12.0 (incluídas no Visual Studio 2013) alteraram os locais do arquivo msbuild, fazendo com que arquivos de destino do Entity Framework sejam inválidos. O resultado é que as tarefas `EntityDeploySplit` e `EntityClean` falham porque não conseguem localizar `Microsoft.Data.Entity.Build.Tasks.dll`. Observe que essa interrupção se deve a uma alteração no conjunto de ferramentas (msbuild/VS), e não por uma mudança no .NET Framework. Ela ocorrerá apenas no upgrade das ferramentas do desenvolvedor, não simplesmente no upgrade do .NET Framework.|  
|Sugestão|Os arquivos de destino do Entity Framework foram corrigidos para trabalhar com o novo layout do msbuild a partir do .NET Framework 4.6. O upgrade para essa versão do Framework corrigirá esse problema. Como alternativa, [esta](http://stackoverflow.com/a/24249247/131944) solução alternativa pode ser usada para aplicar patches diretamente aos arquivos de destino.|  
|Escopo|Principal|  
|Versão|4.5.1-4.6|  
|Tipo|Redirecionando|  
|Analisadores|CD0109|  
  
<a name="diagnostic111"></a>   
## <a name="111-xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a>111: A validação do Esquema XSD agora detecta corretamente as violações de restrições exclusivas se chaves compostas forem usadas e uma chave estiver vazia  
  
|||  
|-|-|  
|Detalhes|As versões do .NET Framework anteriores a 4.6 tinham um bug que fazia com que a validação de XSD não detectasse restrições exclusivas em chaves compostas se uma das chaves estivesse vazia. No .NET Framework 4.6, esse problema foi corrigido. Isso resultará na validação mais correta, mas também pode resultar na não validação de algum XML que anteriormente seria validado.|  
|Sugestão|Se a validação do .NET Framework 4.0 for necessária, o aplicativo de validação poderá se destinar à versão 4.5 (ou anterior) do .NET Framework. No entanto, ao redirecionar para o .NET 4.6, a análise do código deverá ser feita para garantir que não se espere que chaves compostas duplicadas (conforme descrito na descrição desse problema) sejam validadas.|  
|Escopo|Edge|  
|Versão|4.6|  
|Tipo|Redirecionando|  
|Analisadores|CD0111|  
  
<a name="diagnostic112"></a>   
## <a name="112-calling-attributegetcustomattributes-on-an-indexer-property-no-longer-throws-ambiguousmatchexception-if-the-ambiguity-can-be-resolved-by-indexs-type"></a>112: Chamar Attribute.GetCustomAttributes na propriedade de um indexador não vai mais gerar AmbiguousMatchException se a ambiguidade puder ser resolvida pelo tipo do índice  
  
|||  
|-|-|  
|Detalhes|Antes do .NET Framework 4.6, chamar `GetCustomAttribute(s)` na propriedade de um indexador que diferia de outra propriedade apenas pelo tipo do índice resultaria em um `AmbiguousMatchException`. A partir do .NET Framework 4.6, os atributos da propriedade serão corretamente retornados.|  
|Sugestão|Lembre-se de que GetCustomAttribute(s) funcionará com mais frequência agora. Se um aplicativo anteriormente contava com o `AmbiguousMatchException`, a reflexão agora deverá ser usada para procurar explicitamente vários indexadores.|  
|Escopo|Edge|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Attribute.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttribute%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%28System.Reflection.MemberInfo%2CSystem.Type%2CSystem.Boolean%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%29?displayProperty=fullName><br /><br /> <xref:System.Reflection.CustomAttributeExtensions.GetCustomAttributes%60%601%28System.Reflection.MemberInfo%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analisadores|CD0112|  
  
<a name="diagnostic113"></a>   
## <a name="113-intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>113: Não é possível rolar intermitentemente para o item na parte inferior em ItemsControls (como ListBox e DataGrid) ao usar DataTemplates personalizados  
  
|||  
|-|-|  
|Detalhes|Em alguns casos, um bug no .NET Framework 4.5 está fazendo com que ItemsControls (como ListBox, ComboBox, DataGrid, etc.) não rolem para o item na parte inferior ao usar DataTemplates personalizados. Se houver uma tentativa de rolagem pela segunda vez (depois da rolagem de volta), ela funcionará.|  
|Sugestão|Esse problema foi corrigido no .NET Framework 4.5.2 e pode ser solucionado com o upgrade para essa versão (ou uma versão posterior) do .NET Framework. Como alternativa, os usuários ainda podem arrastar as barras de rolagem para os itens finais nessas coleções, mas pode ser necessário tentar duas vezes para obter êxito.|  
|Escopo|Secundário|  
|Versão|4.5-4.5.2|  
|Tipo|Tempo de execução|  
|Analisadores|CD0113|  
  
<a name="diagnostic114"></a>   
## <a name="114-glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-45"></a>114: GlyphRun.ComputeInkBoundingBox() e FormattedText.Extent retornam diferentes valores a partir do .NET 4.5  
  
|||  
|-|-|  
|Detalhes|Foram feitas melhorias em GlyphRun.ComputeInkBoundingBox() e FormattedText.Extent do .NET Framework 4.5 para resolver problemas em que as caixas eram muito pequenas para o glifos contidos em alguns casos no .NET Framework 4.0. Como resultado, algumas caixas delimitadoras serão maiores a partir do .NET Framework 4.5, resultando em diferenças sutis no layout da interface do usuário.|  
|Sugestão|Lembre-se de que alguns tamanhos de caixa delimitadora do glifo aumentaram. Essas alterações geralmente aprimorarão a apresentação e os testes de caixa de clique, mas se o comportamento anterior (anterior ao .NET 4.5) for desejado, ele poderá ser aceito com a adição da seguinte entrada ao arquivo app.config:<br /><br /> `<appsettings> <add key="IncludeAllInkInBoundingBox" value="false"> </appsettings>`|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=fullName><br /><br /> <xref:System.Windows.Media.FormattedText.Extent?displayProperty=fullName>|  
|Analisadores|CD0114|  
  
<a name="diagnostic124"></a>   
## <a name="124-calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>124: Chamar DataGrid.CommitEdit de um manipulador CellEditEnding descarta o foco  
  
|||  
|-|-|  
|Detalhes|Chamar DataGrid.CommitEdit de um dos manipuladores de evento CellEditEnding de DataGrid fará com que DataGrid perca o foco.|  
|Sugestão|Esse bug foi corrigido no .NET Framework 4.5.2, portanto, ele pode ser evitado com a atualização do .NET Framework. Como alternativa, ele pode ser evitado com a nova seleção explícita de DataGrid após chamada de CommitEdit.|  
|Escopo|Edge|  
|Versão|4.5-4.5.2|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName><br /><br /> <xref:System.Windows.Controls.DataGrid.CommitEdit%28System.Windows.Controls.DataGridEditingUnit%2CSystem.Boolean%29?displayProperty=fullName>|  
|Analisadores|CD0124|  
  
<a name="diagnostic125"></a>   
## <a name="125-aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>125: O MVC do ASP.NET agora escapa espaços em cadeias de caracteres passadas por meio dos parâmetros de rota  
  
|||  
|-|-|  
|Detalhes|Para estar em conformidade com a RFC 2396, os espaços nos caminhos de rota agora são escapados na população dos parâmetros de ação usando uma rota. Portanto, enquanto `/controller/action/some data` anteriormente correspondia à rota `/controller/action/{data}` e fornecia `some data` como o parâmetro de dados, ele agora fornecerá `some%20data`.|  
|Sugestão|O código deve ser atualizado para não escapar parâmetros de cadeia de caracteres de uma rota. Se o URI original for necessário, ele poderá ser acessado com a API Request.RequestUri.OriginalString.|  
|Escopo|Secundário|  
|Versão|4.5.2|  
|Tipo|Tempo de execução|  
|APIs afetadas|[System.Web.Http.RouteAttribute](https://msdn.microsoft.com/library/system.web.http.routeattribute(v=vs.118).aspx)|  
|Analisadores|CD0125|  
  
<a name="diagnostic127"></a>   
## <a name="127-vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>127: VB.NET não dá mais suporte à qualificação do namespace parcial para APIs System.Windows  
  
|||  
|-|-|  
|Detalhes|A partir do .NET 4.5.2, os projetos VB.NET não podem especificar as APIs System.Windows com namespaces parcialmente qualificados. Por exemplo, fazer referência a `Windows.Forms.DialogResult` falhará. Em vez disso, o código deve fazer referência ao nome totalmente qualificado (`System.Windows.Forms.DialogResult`) ou importar o namespace específico e simplesmente fazer referência a `DialogResult`.|  
|Sugestão|O código deve ser atualizado para fazer referência as APIs `System.Windows` com nomes simples (e importando o namespace relevante) ou com nomes totalmente qualificados.|  
|Escopo|Secundário|  
|Versão|4.5.2|  
|Tipo|Redirecionando|  
|Analisadores|CD0127|  
  
<a name="diagnostic129"></a>   
## <a name="129-two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>129: Não há suporte para a associação de dados bidirecionais para uma propriedade com um setter público  
  
|||  
|-|-|  
|Detalhes|A tentativa de associar dados a uma propriedade sem um setter público nunca foi um cenário com suporte. A partir do .NET Framework 4.5.1, esse cenário vai gerar uma InvalidOperationException. Observe que essa nova exceção será gerada somente para aplicativos destinados especificamente ao .NET Framework 4.5.1. Se um aplicativo for destinado ao .NET Framework 4.5, a chamada será permitida. Se o aplicativo não for destinado a uma versão específica do .NET Framework, a associação será tratada como unidirecional.|  
|Sugestão|O aplicativo deve ser atualizado para usar a associação unidirecional ou expor publicamente o setter da propriedade. Como alternativa, o direcionamento ao .NET Framework 4.5 fará com que o aplicativo demonstre o comportamento antigo.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Windows.Data.BindingMode?displayProperty=fullName>|  
|Analisadores|CD0129|  
  
<a name="diagnostic130"></a>   
## <a name="130-marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>130: As sobrecargas Marshal.SizeOf e Marshal.PtrToStructure interrompem o código dinâmico  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5.1, a associação dinâmica aos métodos `Marshal.SizeOf` ou `Marshal.PtrToStructure` (por meio do Windows PowerShell, IronPython ou da palavra-chave dinâmica do C#, por exemplo) pode resultar em `MethodInvocationExceptions`, pois novas sobrecargas desses métodos que foram adicionadas podem ser ambíguas para os mecanismos de script.|  
|Sugestão|Atualize os scripts para indicar claramente qual sobrecarga deve ser usada. Normalmente, isso pode ser feito convertendo explicitamente os parâmetros de tipo dos métodos como `System.Type`. Clique [neste link](https://support.microsoft.com/kb/2909958/) para obter mais detalhes e exemplos de como contornar o problema.|  
|Escopo|Secundário|  
|Versão|4.5.1|  
|Tipo|Tempo de execução|  
|Analisadores|CD0130|  
  
<a name="diagnostic131"></a>   
## <a name="131-previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>131: PreviewLostKeyboardFocus será chamado repetidamente se seu manipulador mostrar uma caixa de mensagem do Windows Forms  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.5, chamar `System.Windows.Forms.MessageBox.Show` de um manipulador `UIElement.PreviewLostKeyboardFocus` fará com que o manipulador seja acionado novamente quando a caixa de mensagem for fechada, possivelmente resultando em um loop infinito de caixas de mensagem.|  
|Sugestão|Há duas opções para contornar esse problema.<br /><br /> Ele pode ser evitado chamando `System.Windows.MessageBox.Show` em vez de `System.Windows.Forms.MessageBox.Show`.<br /><br /> Ele pode ser evitado mostrando a caixa de mensagem de um manipulador de eventos `LostKeyboardFocus` (em oposição a um manipulador de eventos `PreviewLostKeyboardFocus`).|  
|Escopo|Edge|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=fullName><br /><br /> <xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=fullName>|  
|Analisadores|CD0131|  
  
<a name="diagnostic133"></a>   
## <a name="133-a-concurrentdictionary-serialized-in-net-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-451-or-452"></a>133: Um ConcurrentDictionary serializado no .NET 4.5 com NetDataContractSerializer não pode ser desserializado pelo .NET 4.5.1 ou 4.5.2  
  
|||  
|-|-|  
|Detalhes|Devido a alterações internas para o tipo, os objetos `System.Collections.Concurrent.ConcurrentDictionary` que são serializados com o .NET Framework 4.5 usando o `NetDataContractSerializer` não podem ser desserializados no .NET Framework 4.5.1 nem no .NET Framework 4.5.2.<br /><br /> Observe que mover para outra direção (serializando com o .NET Framework 4.5 e desserializando com o .NET Framework 4.5) funciona. Da mesma forma, todas as serializações entre versões 4.x funcionam com o .NET Framework 4.6.<br /><br /> A serialização e desserialização com uma única versão do .NET Framework não são afetadas.|  
|Sugestão|Se for necessário serializar e desserializar um ConcurrentDictionary entre o .NET Framework 4.5 e . NET Framework 4.5.1/4.5.2, um serializador alternativo como o serializador DataContractSerializer ou BinaryFormatter deverá ser usado no lugar de NetDataContractSerializer.<br /><br /> Como alternativa, uma vez que esse problema foi resolvido no .NET Framework 4.6, ele pode ser resolvido com o upgrade para essa versão do .NET Framework.|  
|Escopo|Secundário|  
|Versão|4.5.1-4.6|  
|Tipo|Tempo de execução|  
|Analisadores|CD0133|  
  
<a name="diagnostic134"></a>   
## <a name="134-persian-calendar-now-uses-the-hijri-solar-algorithm"></a>134: O calendário persa agora usa o algoritmo solar islâmico  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.6, a classe PersianCalendar usa o algoritmo solar islâmico. Converter datas entre PersianCalendar e outros calendários pode produzir um resultado ligeiramente diferente a partir do .NET Framework 4.6 para datas anteriores a 1800 ou posteriores a 2023 (gregoriano).<br /><br /> Além disso, `PersianCalendar.MinSupportedDateTime` agora é `March 22, 0622 instead of March 21, 0622`.|  
|Sugestão|Lembre-se de que algumas datas anteriores ou posteriores podem ser ligeiramente diferentes quando se usa o PersianCalendar no .NET 4.6. Além disso, ao serializar datas entre processos que podem ser executados em diferentes versões do .NET Framework, não armazene-as como cadeias de caracteres de data PersianCalendar (uma vez que esses valores podem ser diferentes).|  
|Escopo|Secundário|  
|Versão|4.6|  
|Tipo|Tempo de execução|  
|APIs afetadas|<xref:System.Globalization.PersianCalendar?displayProperty=fullName>|  
|Analisadores|CD0134|  
  
<a name="diagnostic138"></a>   
## <a name="138-calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>138: A chamada a CreateDefaultAuthorizationContext com um argumento nulo foi alterada  
  
|||  
|-|-|  
|Detalhes|A implementação de AuthorizationContext retornado por uma chamada a `CreateDefaultAuthorizationContext(IList<IAuthorizationPolicy>)` com um argumento authorizationPolicies nulo mudou sua implementação no .NET Framework 4.6.|  
|Sugestão|Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento. Nesses casos, o comportamento anterior pode ser restaurado de uma destas duas maneiras:<br /><br /> Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6. Para serviços hospedados pelo IIS, use o elemento \<httpRuntime targetFramework="x.x" /> para direcionar a uma versão anterior do .NET Framework.<br /><br /> Adicione a seguinte linha à seção `<appSettings>` de seu arquivo app.config: `<add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />`|  
|Escopo|Secundário|  
|Versão|4.6|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29?displayProperty=fullName>|  
|Analisadores|CD0138|  
  
<a name="diagnostic141"></a>   
## <a name="141-wpf-treeviewitem-must-be-used-within-a-treeview"></a>141: TreeViewItem do WPF deve ser usado em uma TreeView  
  
|||  
|-|-|  
|Detalhes|Uma alteração foi introduzida na versão 4.5 que restringe o uso de elementos TreeViewItem fora de uma TreeView. Isso se manifesta sob as seguintes condições:<br /><br /> O pai visual de TreeViewItem não é um painel. (Um TreeViewItem gerado para uma TreeView terá um painel como seu pai)<br /><br /> O TreeViewItem é um descendente de um VirtualizingStackPanel atuando como o "host de itens" para um controle de lista (ListBox, DataGrid, ListView, etc.). A virtualização não precisa ser habilitada.<br /><br /> O VirtualizingStackPanel é de rolagem por item (`ScrollUnit="Item"`).<br /><br /> Alguém chama `VirtualizingStackPanel.MakeVisible(v)` para rolar um elemento `v` no modo de exibição. Isso pode ser feito explícita ou implicitamente de várias maneiras; talvez a maneira mais comum seja simplesmente clicar em `v` para fornecer a ele o foco do teclado.<br /><br /> A cadeia visual-pai de `v` para o VirtualizingStackPanel percorre o TreeViewItem.<br /><br /> Em outras palavras, isso é visto quando um TreeViewItem é usado fora de uma TreeView e o usuário clica em um descendente do TreeViewItem para colocá-lo no modo de exibição. Se o TreeViewItem não tiver descendentes focalizáveis, você nunca verá esse problema. Um exemplo de situação em que isso é atingido é quando um TreeViewItem é a raiz de um DataTemplate.  Quando esse problema for atingido, haverá uma InvalidCastException que ocorrerá dentro da estrutura do WPF.|  
|Sugestão|Um hotfix será disponibilizado para isso.|  
|Escopo|Secundário|  
|Versão|4.5|  
|Tipo|Tempo de execução|  
|Analisadores|CD0141|  
  
<a name="diagnostic143"></a>   
## <a name="143-x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>143: X509CertificateClaimSet.FindClaims considera todos os claimTypes  
  
|||  
|-|-|  
|Detalhes|Em aplicativos destinados ao .NET Framework 4.6.1, se um conjunto de declarações X509 for inicializado de um certificado que tenha várias entradas DNS em seu campo SAN, o método FindClaims tentará corresponder o argumento claimType a todas as entradas DNS.<br /><br /> Para aplicativos destinados a versões anteriores do .NET Framework, o método FindClaims tentará corresponder o argumento claimType apenas à última entrada DNS.|  
|Sugestão|Essa alteração afeta apenas aplicativos destinados ao .NET Framework 4.6.1. Essa alteração pode ser desabilitada (ou habilitada se destinados a versões anteriores a 4.6.1) com a opção de compatibilidade [DisableMultipleDNSEntries](https://msdn.microsoft.com/library/mt620030%28v=vs.110%29.aspx).|  
|Escopo|Secundário|  
|Versão|4.6.1|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%28System.String%2CSystem.String%29?displayProperty=fullName>|  
|Analisadores|CD0143|  
  
<a name="diagnostic144"></a>   
## <a name="144-applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>144: Application.FilterMessage não é mais gerada para implementações de reentrância de IMessageFilter.PreFilterMessage  
  
|||  
|-|-|  
|Detalhes|Antes do .NET Framework 4.6.1, chamar Application.FilterMessage com uma IMessageFilter.PreFilterMessage que chamou AddMessageFilter ou RemoveMessageFilter (enquanto também chama Application.DoEvents) causaria uma IndexOutOfRangeException.<br /><br /> A partir dos aplicativos destinados ao .NET Framework 4.6.1, essa exceção não é mais gerada e filtros reentrantes, conforme descrito acima, podem ser usados.|  
|Sugestão|Lembre-se de que Application.FilterMessage não vai mais ser gerada para o comportamento reentrante de IMessageFilter.PreFilterMessage descrito acima. Isso afeta apenas aplicativos destinados ao .NET Framework 4.6.1.<br /><br /> Os aplicativos destinados ao .NET Framework 4.6.1 podem recusar essa alteração (ou os aplicativos de Frameworks mais antigos podem aceitar) usando a opção de compatibilidade [DontSupportReentrantFilterMessage](https://msdn.microsoft.com/library/mt620032%28v=vs.110%29.aspx).|  
|Escopo|Edge|  
|Versão|4.6.1|  
|Tipo|Redirecionando|  
|APIs afetadas|<xref:System.Windows.Forms.Application.FilterMessage%28System.Windows.Forms.Message%40%29?displayProperty=fullName>|  
|Analisadores|CD0144|  
  
<a name="diagnostic145"></a>   
## <a name="145-currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>145: CurrentCulture não é preservada entre operações do Dispatcher do WPF  
  
|||  
|-|-|  
|Detalhes|A partir do .NET Framework 4.6, as alterações em CurrentCulture ou CurrentUICulture feitas em um [Dispatcher](https://msdn.microsoft.com/library/system.windows.threading.dispatcher%28v=vs.110%29.aspx) serão perdidas ao final dessa operação do dispatcher. Da mesma forma, as alterações em CurrentCulture ou CurrentUICulture feitas fora de uma operação de Dispatcher podem não ser refletidas quando operação é executada.<br /><br /> Falando de modo prático, isso significa que as alterações em CurrentCulture e CurrentUICulture podem não fluir entre os retornos de chamada da interface de usuário do WPF e outro código em um aplicativo WPF.<br /><br /> Isso se deve a uma alteração em [ExecutionContext](https://msdn.microsoft.com/library/system.threading.executioncontext%28v=vs.110%29.aspx) que faz com que CurrentCulture e CurrentUICulture sejam armazenados no contexto de execução a partir dos aplicativos destinados ao .NET Framework 4.6. As operações de dispatcher do WPF armazenam o contexto de execução usado para começar a operação e restaurar o contexto anterior quando a operação é concluída. Como CurrentCulture e CurrentUICulture agora fazem parte desse contexto, as alterações neles em uma operação de dispatcher não são persistidas fora da operação.|  
|Sugestão|Os aplicativos afetados por essa alteração poderão contornar esse problema ao armazenar CurrentCulture ou CurrentUICulture desejado em um campo e verificar em todos os corpos da operação de Dispatcher (incluindo manipuladores de retorno de chamada do evento de interface do usuário) se CurrentCulture e CurrentUICulture corretos foram definidos. Como alternativa, como a alteração de ExecutionContext subjacente a essa alteração do WPF afeta apenas aplicativos destinados ao .NET Framework 4.6 ou mais recente, essa interrupção poderá ser evitada destinando-os ao .NET Framework 4.5.2.|  
|Escopo|Secundário|  
|Versão|4.6|  
|Tipo|Redirecionando|  
|Analisadores|CD0145|
