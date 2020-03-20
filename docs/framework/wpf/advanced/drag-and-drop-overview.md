---
title: Visão geral de arrastar e soltar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
ms.openlocfilehash: dd42af77300a7a93bbcbfa4c8f1fc365fc3f5da1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185972"
---
# <a name="drag-and-drop-overview"></a>Visão geral de arrastar e soltar
Este tópico fornece uma visão geral do suporte ao recurso do tipo "arrastar e soltar" em aplicativos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Normalmente, o recurso do tipo "arrastar e soltar" se refere a um método de transferência de dados que envolve o uso de um mouse (ou algum outro dispositivo apontador) para selecionar um ou mais objetos, arrastá-los sobre um destino de soltar desejado na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e soltá-los.  

<a name="Drag_and_Drop_Support"></a>
## <a name="drag-and-drop-support-in-wpf"></a>Suporte ao recurso do tipo "arrastar e soltar" no WPF  
 Normalmente, as operações do tipo "arrastar e soltar" envolvem duas partes: uma origem do arrasto da qual o objeto arrastado se origina e um destino de soltar que recebe o objeto solto.  A origem do arrasto e o destino de soltar podem ser elementos de interface do usuário no mesmo ou em outro aplicativo.  
  
 O tipo e o número de objetos que podem ser manipulados com o recurso do tipo "arrastar e soltar" é completamente arbitrário. Por exemplo, arquivos, pastas e seleções de conteúdo são alguns dos objetos mais comuns manipulados por meio de operações do tipo "arrastar e soltar".  
  
 As ações específicas realizadas durante uma operação do tipo "arrastar e soltar" são específicas ao aplicativo e, frequentemente, determinadas pelo contexto.  Por exemplo, arrastar uma seleção de arquivos de uma pasta para outra no mesmo dispositivo de armazenamento move os arquivos por padrão, enquanto arrastar arquivos de um compartilhamento de Convenção de Nomeação Universal (UNC) para uma pasta local copia os arquivos por padrão.  
  
 As funcionalidades do tipo "arrastar e soltar" fornecidas pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] foram projetadas para serem altamente flexíveis e personalizáveis, a fim de dar suporte a uma ampla variedade de cenários de operações do tipo "arrastar e soltar".  As operações do tipo "arrastar e soltar" dão suporte à manipulação de objetos em um único aplicativo ou entre diferentes aplicativos. Arrastar-e-soltar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entre aplicativos e outros aplicativos do Windows também é totalmente suportado.  
  
 Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> qualquer ou pode participar de arrastar e soltar. Os eventos e métodos necessários para operações <xref:System.Windows.DragDrop> de arrastar e soltar são definidos na classe. As <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> classes e as classes <xref:System.Windows.DragDrop> contêm pseudônimos para os eventos anexados <xref:System.Windows.UIElement> para <xref:System.Windows.ContentElement> que os eventos apareçam na lista de membros da classe quando um ou for herdado como elemento base. Os manipuladores de eventos que estão conectados a <xref:System.Windows.DragDrop> esses eventos são anexados ao evento anexado subjacente e recebem a mesma instância de dados do evento. Para saber mais, confira o evento <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Operações do tipo "arrastar e soltar" OLE não funcionarão se você estiver na zona da Internet.  
  
<a name="Data_Transfer"></a>
## <a name="data-transfer"></a>Transferência de dados  
 Arrastar e soltar faz parte da área de transferência de dados mais geral. A transferência de dados inclui operações do tipo "arrastar e soltar" e copiar e colar. Uma operação do tipo "arrastar e soltar" é análoga a uma operação de copiar e colar ou de recortar e colar, que é usada para transferir dados de um objeto ou aplicativo para outro usando a área de transferência do sistema. Os dois tipos de operações exigem:  
  
- Um objeto de origem que fornece os dados.  
  
- Uma maneira de armazenar temporariamente os dados transferidos.  
  
- Um objeto de destino que recebe os dados.  
  
 Em uma operação de cópia e cola, a área de transferência do sistema é usada para armazenar temporariamente os dados transferidos; em uma operação de arrastar <xref:System.Windows.DataObject> e soltar, um é usado para armazenar os dados. Conceitualmente, um objeto de dados consiste em <xref:System.Object> um ou mais pares de um que contém os dados reais e um identificador de formato de dados correspondente.  
  
 A fonte de arrasto inicia uma operação de <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> arrastar e soltar chamando o método estático e passando os dados transferidos para ele. O <xref:System.Windows.DragDrop.DoDragDrop%2A> método envolverá automaticamente os <xref:System.Windows.DataObject> dados em um, se necessário. Para obter maior controle sobre o formato de <xref:System.Windows.DataObject> dados, você <xref:System.Windows.DragDrop.DoDragDrop%2A> pode envolver os dados em um antes de passá-los para o método. O alvo de queda é responsável <xref:System.Windows.DataObject>por extrair os dados do . Para obter mais informações sobre como trabalhar com objetos de dados, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 A origem e o destino de uma operação do tipo "arrastar e soltar" são elementos de interface do usuário; no entanto, os dados que realmente são transferidos, normalmente, não têm uma representação visual. É possível escrever um código para fornecer uma representação visual dos dados que são arrastados, assim como ocorre ao arrastar arquivos no Windows Explorer. Por padrão, comentários são fornecidos ao usuário com a alteração do cursor para representar o efeito que a operação do tipo "arrastar e soltar" terá sobre os dados, por exemplo, se os dados serão movidos ou copiados.  
  
### <a name="drag-and-drop-effects"></a>Efeitos das operações do tipo "arrastar e soltar"  
 Operações do tipo "arrastar e soltar" podem ter efeitos diferentes nos dados transferidos. Por exemplo, é possível copiar os dados ou movê-los. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]define uma <xref:System.Windows.DragDropEffects> enumeração que você pode usar para especificar o efeito de uma operação de arrastar e soltar. Na fonte de arrasto, você pode especificar <xref:System.Windows.DragDrop.DoDragDrop%2A> os efeitos que a fonte permitirá no método. No alvo de queda, você pode especificar <xref:System.Windows.DragEventArgs.Effects%2A> o <xref:System.Windows.DragEventArgs> efeito que o alvo pretende na propriedade da classe. Quando o alvo de queda <xref:System.Windows.DragDrop.DragOver> especifica o efeito pretendido no evento, <xref:System.Windows.DragDrop.GiveFeedback> essa informação é transmitida de volta para a fonte de arrasto no evento. A origem do arrasto usa essas informações para informar ao usuário o efeito que o destino de soltar pretende ter sobre os dados. Quando os dados são descartados, a meta de <xref:System.Windows.DragDrop.Drop> queda especifica seu efeito real no evento. Essa informação é passada de volta para a <xref:System.Windows.DragDrop.DoDragDrop%2A> fonte de arrasto como o valor de retorno do método. Se o destino de soltar retornar um efeito que não está na lista `allowedEffects` da origem do arrasto, a operação do tipo "arrastar e soltar" será cancelada sem nenhuma transferência de dados.  
  
 É importante lembrar que, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.DragDropEffects> em , os valores são usados apenas para fornecer comunicação entre a fonte de arrasto e o alvo de queda em relação aos efeitos da operação arrastar e soltar. O efeito real da operação do tipo "arrastar e soltar" depende da escrita do código apropriado no aplicativo.  
  
 Por exemplo, o destino de soltar pode especificar que o efeito de soltar dados nele é mover os dados. No entanto, para mover os dados, ele deve ser adicionado ao elemento de destino e removido do elemento de origem. O elemento de origem pode indicar que ele permite a movimentação dos dados, mas se você não fornecer o código para remover os dados do elemento de origem, o resultado final será que os dados serão copiados e não movidos.  
  
<a name="Drag_and_Drop_Events"></a>
## <a name="drag-and-drop-events"></a>Eventos das operações do tipo "arrastar e soltar"  
 As operações do tipo "arrastar e soltar" dão suporte a um modelo controlado por evento.  A origem do arrasto e o destino de soltar usam um conjunto padrão de eventos para manipular operações do tipo "arrastar e soltar".  As tabelas a seguir resumem os eventos padrão das operações do tipo "arrastar e soltar". Estes são eventos <xref:System.Windows.DragDrop> anexados na classe. Para obter mais informações sobre eventos anexados, consulte [Visão geral dos eventos anexados](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Eventos de origem do arrasto  
  
|Evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Esse evento ocorre continuamente durante uma operação do tipo "arrastar e soltar" e permite que a origem de soltar forneça informações de comentários ao usuário. Geralmente, esses comentários são fornecidos com a alteração da aparência do ponteiro do mouse para indicar os efeitos permitidos pelo destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Esse evento ocorre quando há uma alteração nos estados do teclado ou do botão do mouse durante uma do tipo "arrastar e soltar" e permite que a origem de soltar cancele a operação do tipo "arrastar e soltar", dependendo dos estados da tecla e do botão. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Versão de <xref:System.Windows.DragDrop.GiveFeedback>tunelamento de .|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Versão de <xref:System.Windows.DragDrop.QueryContinueDrag>tunelamento de .|  
  
### <a name="drop-target-events"></a>Eventos de destino de soltar  
  
|Evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Esse evento ocorre quando um objeto é arrastado para os limites do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragLeave>|Esse evento ocorre quando um objeto é arrastado para fora dos limites do destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragOver>|Esse evento ocorre continuamente enquanto um objeto é arrastado (movido) dentro do limite do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.Drop>|Esse evento ocorre quando um objeto é solto no destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Versão de <xref:System.Windows.DragDrop.DragEnter>tunelamento de .|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Versão de <xref:System.Windows.DragDrop.DragLeave>tunelamento de .|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Versão de <xref:System.Windows.DragDrop.DragOver>tunelamento de .|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Versão de <xref:System.Windows.DragDrop.Drop>tunelamento de .|  
  
 Para manipular eventos das operações do tipo "arrastar e soltar" em instâncias de um objeto, adicione manipuladores para os eventos listados nas tabelas anteriores. Para manipular eventos das operações do tipo "arrastar e soltar" no nível de classe, substitua os métodos virtuais On*Event e On\*PreviewEvent correspondentes. Para obter mais informações, consulte [Manipulação de classes de eventos roteados por classes base de controle](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>
## <a name="implementing-drag-and-drop"></a>Implementando operações do tipo "arrastar e soltar"  
 Um elemento de interface do usuário pode ser uma origem do arrasto, um destino de soltar ou ambos. Para implementar uma operação básica do tipo "arrastar e soltar", um código é escrito para iniciar a operação do tipo "arrastar e soltar" e processar os dados soltos. É possível melhorar essa experiência de "arrastar e soltar" manipulando eventos opcionais das operações do tipo "arrastar e soltar".  
  
 Para implementar uma operação básica do tipo "arrastar e soltar", você realizará as seguintes tarefas:  
  
- Identificar o elemento que será uma origem do arrasto. Uma fonte de <xref:System.Windows.UIElement> arrasto <xref:System.Windows.ContentElement>pode ser a ou a .  
  
- Criar um manipulador de eventos na origem do arrasto que iniciará a operação do tipo "arrastar e soltar". O evento é <xref:System.Windows.UIElement.MouseMove> tipicamente o evento.  
  
- No manipulador de eventos de <xref:System.Windows.DragDrop.DoDragDrop%2A> origem de arrasto, chame o método para iniciar a operação de arrastar e soltar. Na <xref:System.Windows.DragDrop.DoDragDrop%2A> chamada, especifique a fonte de arrasto, os dados a serem transferidos e os efeitos permitidos.  
  
- Identificar o elemento que será um destino de soltar. Um alvo de <xref:System.Windows.UIElement> queda pode ser ou um <xref:System.Windows.ContentElement>.  
  
- No alvo de queda, defina a <xref:System.Windows.UIElement.AllowDrop%2A> propriedade para `true`.  
  
- No destino de queda, crie um <xref:System.Windows.DragDrop.Drop> manipulador de eventos para processar os dados descartados.  
  
- No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, extraia <xref:System.Windows.DataObject.GetDataPresent%2A> os <xref:System.Windows.DataObject.GetData%2A> dados do <xref:System.Windows.DragEventArgs> usando os métodos.  
  
- No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, use os dados para executar a operação de arrastar e soltar desejada.  
  
 Você pode melhorar sua implementação de arrastar <xref:System.Windows.DataObject> e soltar criando um personalizado e manipulando eventos de origem de arrasto e destino de queda opcionais, conforme mostrado nas tarefas a seguir:  
  
- Para transferir dados personalizados ou vários <xref:System.Windows.DataObject> itens de <xref:System.Windows.DragDrop.DoDragDrop%2A> dados, crie um para passar para o método.  
  
- Para executar ações adicionais durante <xref:System.Windows.DragDrop.DragEnter> <xref:System.Windows.DragDrop.DragOver>um <xref:System.Windows.DragDrop.DragLeave> arrasto, manuseie o , e eventos no alvo de queda.  
  
- Para alterar a aparência do ponteiro <xref:System.Windows.DragDrop.GiveFeedback> do mouse, manuseie o evento na fonte de arrasto.  
  
- Para alterar a forma como a operação de <xref:System.Windows.DragDrop.QueryContinueDrag> arrastar e soltar é cancelada, manuseie o evento na fonte drag.  
  
<a name="Drag_And_Drop_Example"></a>
## <a name="drag-and-drop-example"></a>Exemplo de operação do tipo "arrastar e soltar"  
 Esta seção descreve como implementar arrastar e <xref:System.Windows.Shapes.Ellipse> soltar para um elemento. É <xref:System.Windows.Shapes.Ellipse> uma fonte de arrasto e um alvo de queda. Os dados transferidos são a representação <xref:System.Windows.Shapes.Shape.Fill%2A> de string da propriedade da elipse. O XAML a <xref:System.Windows.Shapes.Ellipse> seguir mostra o elemento e os eventos relacionados ao arrasto e queda que ele lida. Para obter etapas completas de como implementar uma operação do tipo "arrastar e soltar", consulte [Passo a passo: Habilitando operações de arrastar e soltar em um controle de usuário](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Habilitando um elemento a ser uma origem do arrasto  
 Um objeto que é uma origem do arrasto é responsável por:  
  
- Identificar quando ocorre uma operação de arrastar.  
  
- Iniciar a operação do tipo "arrastar e soltar".  
  
- Identificar os dados a serem transferidos.  
  
- Especificar os efeitos que a operação do tipo "arrastar e soltar" tem permissão para ter sobre os dados transferidos.  
  
 A origem do arrasto também pode fornecer comentários ao usuário sobre as ações permitidas (mover, copiar, nenhuma) e pode cancelar a operação do tipo "arrastar e soltar" de acordo com a entrada adicional do usuário, como pressionar a tecla ESC durante a operação de arrastar.  
  
 É responsabilidade do seu aplicativo determinar quando ocorre um arrasto e, em seguida, iniciar a operação de arrastar e soltar ligando para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método. Normalmente, é quando <xref:System.Windows.UIElement.MouseMove> ocorre um evento sobre o elemento a ser arrastado enquanto um botão do mouse é pressionado. O exemplo a seguir mostra como iniciar uma <xref:System.Windows.UIElement.MouseMove> operação de <xref:System.Windows.Shapes.Ellipse> arrastar e soltar do manipulador de eventos de um elemento para torná-lo uma fonte de arrasto. Os dados transferidos são a representação <xref:System.Windows.Shapes.Shape.Fill%2A> de string da propriedade da elipse.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Dentro do <xref:System.Windows.UIElement.MouseMove> manipulador de <xref:System.Windows.DragDrop.DoDragDrop%2A> eventos, chame o método para iniciar a operação de arrastar e soltar. O <xref:System.Windows.DragDrop.DoDragDrop%2A> método leva três parâmetros:  
  
- `dragSource`– Uma referência ao objeto de dependência que é a fonte dos dados transferidos; esta é tipicamente a <xref:System.Windows.UIElement.MouseMove> fonte do evento.  
  
- `data`- Um objeto que contém os <xref:System.Windows.DataObject>dados transferidos, embrulhados em um .  
  
- `allowedEffects`- Um <xref:System.Windows.DragDropEffects> dos valores de enumeração que especifica os efeitos permitidos da operação de arrastar e soltar.  
  
 Qualquer objeto serializável pode ser passado no parâmetro `data`. Se os dados ainda não <xref:System.Windows.DataObject>estão embrulhados em um, <xref:System.Windows.DataObject>ele será automaticamente embrulhado em um novo . Para passar vários itens de dados, <xref:System.Windows.DataObject> você deve criar <xref:System.Windows.DragDrop.DoDragDrop%2A> o mesmo e passá-lo para o método. Para obter mais informações, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 O parâmetro `allowedEffects` é usado para especificar o que a origem do arrasto permitirá que o destino de soltar faça com os dados transferidos. Os valores comuns <xref:System.Windows.DragDropEffects.Copy>para <xref:System.Windows.DragDropEffects.Move>uma <xref:System.Windows.DragDropEffects.All>fonte de arrasto são , e .  
  
> [!NOTE]
> O destino de soltar também pode especificar quais efeitos ele pretender ter em resposta aos dados soltos. Por exemplo, se a meta de queda não reconhecer o tipo de dados a <xref:System.Windows.DragDropEffects.None>ser descartado, ele pode recusar os dados definindo seus efeitos permitidos para . Ele normalmente faz <xref:System.Windows.DragDrop.DragOver> isso em seu manipulador de eventos.  
  
 Uma fonte de arrasto <xref:System.Windows.DragDrop.GiveFeedback> <xref:System.Windows.DragDrop.QueryContinueDrag> pode, opcionalmente, lidar com os eventos. Esses eventos têm manipuladores padrão que são usados, a menos que você marque os eventos como manipulados. Normalmente, você ignorará esses eventos, a menos que tenha uma necessidade específica de alterar seu comportamento padrão.  
  
 O <xref:System.Windows.DragDrop.GiveFeedback> evento é levantado continuamente enquanto a fonte de arrasto está sendo arrastada. O manipulador padrão para esse evento verifica se a origem do arrasto está sobre um destino de soltar válido. Se estiver, ela verificará os efeitos permitidos do destino de soltar. Em seguida, ela fornece comentários ao usuário final sobre os efeitos de soltar permitidos. Geralmente, isso é feito com a alteração do cursor do mouse para um cursor do tipo não soltar, copiar ou mover. Você só deverá manipular esse evento se precisar usar cursores personalizados para fornecer comentários ao usuário. Se você manipular esse evento, lembre-se de marcá-lo como manipulado para que o manipulador padrão não substitua o manipulador.  
  
 O <xref:System.Windows.DragDrop.QueryContinueDrag> evento é levantado continuamente enquanto a fonte de arrasto está sendo arrastada. Você pode manipular esse evento para determinar qual ação encerra a operação do tipo "arrastar e soltar", de acordo com o estado das teclas ESC, SHIFT, CTRL e ALT, bem como o estado dos botões do mouse. O manipulador padrão desse evento cancela a operação do tipo "arrastar e soltar" se a tecla ESC é pressionada e solta os dados se o botão do mouse é liberado.  
  
> [!CAUTION]
> Esses eventos são acionados continuamente durante a operação do tipo "arrastar e soltar". Portanto, você deve evitar tarefas com uso intensivo de recursos nos manipuladores de eventos.  Por exemplo, use um cursor armazenado em cache em <xref:System.Windows.DragDrop.GiveFeedback> vez de criar um novo cursor cada vez que o evento for levantado.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Habilitando um elemento a ser um destino de soltar  
 Um objeto que é um destino de soltar é responsável por:  
  
- Especificar se ele é um destino de soltar válido.  
  
- Responder à origem do arrasto quando ele é arrastado para o destino.  
  
- Verificar se os dados transferidos estão em um formato que pode ser recebido.  
  
- Processar os dados soltos.  
  
 Para especificar que um elemento é <xref:System.Windows.UIElement.AllowDrop%2A> um `true`alvo de queda, você define sua propriedade para . Em seguida, os eventos de destino de soltar serão acionados no elemento, para que você possa manipulá-los. Durante uma operação do tipo "arrastar e soltar", ocorre a seguinte sequência de eventos no destino de soltar:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> ou <xref:System.Windows.DragDrop.Drop>  
  
 O <xref:System.Windows.DragDrop.DragEnter> evento ocorre quando os dados são arrastados para o limite do alvo de queda. Normalmente, esse evento é manipulado para fornecer uma visualização dos efeitos da operação do tipo "arrastar e soltar", se apropriado para o aplicativo. Não defina <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> a <xref:System.Windows.DragDrop.DragEnter> propriedade no evento, pois ela <xref:System.Windows.DragDrop.DragOver> será substituída no evento.  
  
 O exemplo a <xref:System.Windows.DragDrop.DragEnter> seguir mostra <xref:System.Windows.Shapes.Ellipse> o manipulador de eventos para um elemento. Este código visualiza os efeitos da operação arrastar e <xref:System.Windows.Shapes.Shape.Fill%2A> soltar salvando o pincel atual. Em seguida, <xref:System.Windows.DataObject.GetDataPresent%2A> ele usa <xref:System.Windows.DataObject> o método para verificar se o arrasto sobre a <xref:System.Windows.Media.Brush>elipse contém dados de seqüência que podem ser convertidos em um . Nesse caso, os dados são <xref:System.Windows.DataObject.GetData%2A> extraídos usando o método. Em seguida, é <xref:System.Windows.Media.Brush> convertido em um e aplicado à elipse. A mudança é revertida <xref:System.Windows.DragDrop.DragLeave> no manipulador de eventos. Se os dados não puderem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação será realizada.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 O <xref:System.Windows.DragDrop.DragOver> evento ocorre continuamente enquanto os dados são arrastados sobre o alvo de queda. Este evento é emparelhado <xref:System.Windows.DragDrop.GiveFeedback> com o evento na fonte drag. No <xref:System.Windows.DragDrop.DragOver> manipulador de eventos, você <xref:System.Windows.DataObject.GetDataPresent%2A> <xref:System.Windows.DataObject.GetData%2A> normalmente usa os métodos e métodos para verificar se os dados transferidos estão em um formato que o destino de queda pode processar. Também é possível verificar se teclas modificadoras são pressionadas, o que geralmente indica se o usuário pretende executar uma ação de mover ou copiar. Depois que essas verificações <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> são realizadas, você define a propriedade para notificar a fonte de arrasto que efeito a queda dos dados terá. A fonte drag recebe <xref:System.Windows.DragDrop.GiveFeedback> essas informações no evento args, e pode definir um cursor apropriado para dar feedback ao usuário.  
  
 O exemplo a <xref:System.Windows.DragDrop.DragOver> seguir mostra <xref:System.Windows.Shapes.Ellipse> o manipulador de eventos para um elemento. Este código verifica se <xref:System.Windows.DataObject> o arrasto sobre a elipse contém dados <xref:System.Windows.Media.Brush>de seqüência que podem ser convertidos em um . Se assim for, <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> ele <xref:System.Windows.DragDropEffects.Copy>define a propriedade para . Isso indica à origem do arrasto que os dados podem ser copiados para a elipse. Se os dados não puderem <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> ser convertidos <xref:System.Windows.DragDropEffects.None>em a, <xref:System.Windows.Media.Brush>a propriedade será definida como . Isso indica à origem do arrasto que a elipse não é um destino de soltar válido para os dados.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 O <xref:System.Windows.DragDrop.DragLeave> evento ocorre quando os dados são arrastados para fora do limite do alvo sem serem descartados. Você lida com este evento para desfazer qualquer coisa que você fez no <xref:System.Windows.DragDrop.DragEnter> manipulador de eventos.  
  
 O exemplo a <xref:System.Windows.DragDrop.DragLeave> seguir mostra <xref:System.Windows.Shapes.Ellipse> o manipulador de eventos para um elemento. Este código desfaz a <xref:System.Windows.DragDrop.DragEnter> visualização realizada no <xref:System.Windows.Media.Brush> manipulador de eventos aplicando o salvo na elipse.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 O <xref:System.Windows.DragDrop.Drop> evento ocorre quando os dados são descartados sobre a meta de queda; por padrão, isso acontece quando o botão do mouse é liberado. No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, <xref:System.Windows.DataObject.GetData%2A> você usa o método <xref:System.Windows.DataObject> para extrair os dados transferidos do e executar qualquer processamento de dados que seu aplicativo exija. O <xref:System.Windows.DragDrop.Drop> evento encerra a operação de arrastar e soltar.  
  
 O exemplo a <xref:System.Windows.DragDrop.Drop> seguir mostra <xref:System.Windows.Shapes.Ellipse> o manipulador de eventos para um elemento. Este código aplica os efeitos da operação arrastar e soltar e é <xref:System.Windows.DragDrop.DragEnter> semelhante ao código no manipulador de eventos. Ele verifica se <xref:System.Windows.DataObject> o ser arrastado sobre a elipse contém dados <xref:System.Windows.Media.Brush>de seqüência que podem ser convertidos em um . Se assim for, o <xref:System.Windows.Media.Brush> é aplicado à elipse. Se os dados não puderem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação será realizada.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Clipboard>
- [Instruções passo a passo: habilitando arrastar e soltar em um controle de usuário](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tópicos de como fazer](drag-and-drop-how-to-topics.md)
- [Arrastar e soltar](drag-and-drop.md)
