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
ms.openlocfilehash: 0a2fae2acd2b190e6133c1f02010a7e3d35bba67
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663348"
---
# <a name="drag-and-drop-overview"></a>Visão geral de arrastar e soltar
Este tópico fornece uma visão geral do suporte ao recurso do tipo "arrastar e soltar" em aplicativos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Normalmente, o recurso do tipo "arrastar e soltar" se refere a um método de transferência de dados que envolve o uso de um mouse (ou algum outro dispositivo apontador) para selecionar um ou mais objetos, arrastá-los sobre um destino de soltar desejado na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e soltá-los.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Suporte ao recurso do tipo "arrastar e soltar" no WPF  
 Normalmente, as operações do tipo "arrastar e soltar" envolvem duas partes: uma origem do arrasto da qual o objeto arrastado se origina e um destino de soltar que recebe o objeto solto.  A origem do arrasto e o destino de soltar podem ser elementos de interface do usuário no mesmo ou em outro aplicativo.  
  
 O tipo e o número de objetos que podem ser manipulados com o recurso do tipo "arrastar e soltar" é completamente arbitrário. Por exemplo, arquivos, pastas e seleções de conteúdo são alguns dos objetos mais comuns manipulados por meio de operações do tipo "arrastar e soltar".  
  
 As ações específicas realizadas durante uma operação do tipo "arrastar e soltar" são específicas ao aplicativo e, frequentemente, determinadas pelo contexto.  Por exemplo, arrastar uma seleção de arquivos de uma pasta para outra no mesmo dispositivo de armazenamento move os arquivos por padrão, enquanto arrastar arquivos de um compartilhamento do [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] para uma pasta local copia os arquivos por padrão.  
  
 As funcionalidades do tipo "arrastar e soltar" fornecidas pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] foram projetadas para serem altamente flexíveis e personalizáveis, a fim de dar suporte a uma ampla variedade de cenários de operações do tipo "arrastar e soltar".  As operações do tipo "arrastar e soltar" dão suporte à manipulação de objetos em um único aplicativo ou entre diferentes aplicativos. Arrastar e soltar entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos e outros aplicativos do Windows também é totalmente suportado.  
  
 Na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> pode participar de arrastar e soltar. Os eventos e métodos necessários para operações de arrastar e soltar são definidas na <xref:System.Windows.DragDrop> classe. O <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> classes contêm aliases para o <xref:System.Windows.DragDrop> eventos anexados, para que os eventos são exibidos na classe quando a lista de membros um <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> é herdado como um elemento base. Manipuladores de eventos que estão associadas a esses eventos são anexados ao subjacente <xref:System.Windows.DragDrop> evento anexado e receber a mesma instância de dados do evento. Para saber mais, confira o evento <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Operações do tipo "arrastar e soltar" OLE não funcionarão se você estiver na zona da Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transferência de dados  
 Arrastar e soltar faz parte da área de transferência de dados mais geral. A transferência de dados inclui operações do tipo "arrastar e soltar" e copiar e colar. Uma operação do tipo "arrastar e soltar" é análoga a uma operação de copiar e colar ou de recortar e colar, que é usada para transferir dados de um objeto ou aplicativo para outro usando a área de transferência do sistema. Os dois tipos de operações exigem:  
  
- Um objeto de origem que fornece os dados.  
  
- Uma maneira de armazenar temporariamente os dados transferidos.  
  
- Um objeto de destino que recebe os dados.  
  
 Em uma operação de copiar e colar, a área de transferência do sistema é usada para armazenar temporariamente os dados transferidos; em uma operação de arrastar e soltar, um <xref:System.Windows.DataObject> é usado para armazenar os dados. Conceitualmente, um objeto de dados consiste em um ou mais pares de um <xref:System.Object> que contém os dados reais e um identificador de formato de dados correspondente.  
  
 A origem do arrasto inicia uma operação de arrastar e soltar chamando estático <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> método e passar os dados transferidos para ele. O <xref:System.Windows.DragDrop.DoDragDrop%2A> método encapsulará automaticamente os dados em um <xref:System.Windows.DataObject> se necessário. Para obter maior controle sobre o formato de dados, você pode encapsular os dados em um <xref:System.Windows.DataObject> antes de passá-lo para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método. O destino de soltar é responsável por extrair os dados a partir de <xref:System.Windows.DataObject>. Para obter mais informações sobre como trabalhar com objetos de dados, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 A origem e o destino de uma operação do tipo "arrastar e soltar" são elementos de interface do usuário; no entanto, os dados que realmente são transferidos, normalmente, não têm uma representação visual. É possível escrever um código para fornecer uma representação visual dos dados que são arrastados, assim como ocorre ao arrastar arquivos no Windows Explorer. Por padrão, comentários são fornecidos ao usuário com a alteração do cursor para representar o efeito que a operação do tipo "arrastar e soltar" terá sobre os dados, por exemplo, se os dados serão movidos ou copiados.  
  
### <a name="drag-and-drop-effects"></a>Efeitos das operações do tipo "arrastar e soltar"  
 Operações do tipo "arrastar e soltar" podem ter efeitos diferentes nos dados transferidos. Por exemplo, é possível copiar os dados ou movê-los. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] define um <xref:System.Windows.DragDropEffects> enumeração que você pode usar para especificar o efeito de uma operação de arrastar e soltar. Na origem do arrasto, você pode especificar os efeitos que a origem permitirá no <xref:System.Windows.DragDrop.DoDragDrop%2A> método. No destino de soltar, você pode especificar o efeito pretendido pelo destino na <xref:System.Windows.DragEventArgs.Effects%2A> propriedade do <xref:System.Windows.DragEventArgs> classe. Quando o destino de soltar especifica seu efeito pretendido na <xref:System.Windows.DragDrop.DragOver> evento, essas informações são passadas de volta para a origem do arrasto no <xref:System.Windows.DragDrop.GiveFeedback> eventos. A origem do arrasto usa essas informações para informar ao usuário o efeito que o destino de soltar pretende ter sobre os dados. Quando os dados são descartados, o destino de soltar especifica seu efeito real no <xref:System.Windows.DragDrop.Drop> eventos. Que informações são passadas para a origem do arrasto como o valor de retorno de <xref:System.Windows.DragDrop.DoDragDrop%2A> método. Se o destino de soltar retornar um efeito que não está na lista `allowedEffects` da origem do arrasto, a operação do tipo "arrastar e soltar" será cancelada sem nenhuma transferência de dados.  
  
 É importante lembrar que, no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o <xref:System.Windows.DragDropEffects> valores só são usados para fornecer comunicação entre a origem do arrasto e o destino de soltar sobre os efeitos da operação de arrastar e soltar. O efeito real da operação do tipo "arrastar e soltar" depende da escrita do código apropriado no aplicativo.  
  
 Por exemplo, o destino de soltar pode especificar que o efeito de soltar dados nele é mover os dados. No entanto, para mover os dados, ele deve ser adicionado ao elemento de destino e removido do elemento de origem. O elemento de origem pode indicar que ele permite a movimentação dos dados, mas se você não fornecer o código para remover os dados do elemento de origem, o resultado final será que os dados serão copiados e não movidos.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Eventos das operações do tipo "arrastar e soltar"  
 As operações do tipo "arrastar e soltar" dão suporte a um modelo controlado por evento.  A origem do arrasto e o destino de soltar usam um conjunto padrão de eventos para manipular operações do tipo "arrastar e soltar".  As tabelas a seguir resumem os eventos padrão das operações do tipo "arrastar e soltar". Esses são eventos anexados no <xref:System.Windows.DragDrop> classe. Para obter mais informações sobre eventos anexados, consulte [Visão geral dos eventos anexados](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Eventos de origem do arrasto  
  
|evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Esse evento ocorre continuamente durante uma operação do tipo "arrastar e soltar" e permite que a origem de soltar forneça informações de comentários ao usuário. Geralmente, esses comentários são fornecidos com a alteração da aparência do ponteiro do mouse para indicar os efeitos permitidos pelo destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Esse evento ocorre quando há uma alteração nos estados do teclado ou do botão do mouse durante uma do tipo "arrastar e soltar" e permite que a origem de soltar cancele a operação do tipo "arrastar e soltar", dependendo dos estados da tecla e do botão. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Versão de túnel de <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Versão de túnel de <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Eventos de destino de soltar  
  
|evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Esse evento ocorre quando um objeto é arrastado para os limites do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragLeave>|Esse evento ocorre quando um objeto é arrastado para fora dos limites do destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragOver>|Esse evento ocorre continuamente enquanto um objeto é arrastado (movido) dentro do limite do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.Drop>|Esse evento ocorre quando um objeto é solto no destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Versão de túnel de <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Versão de túnel de <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Versão de túnel de <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Versão de túnel de <xref:System.Windows.DragDrop.Drop>.|  
  
 Para manipular eventos das operações do tipo "arrastar e soltar" em instâncias de um objeto, adicione manipuladores para os eventos listados nas tabelas anteriores. Para manipular eventos das operações do tipo "arrastar e soltar" no nível de classe, substitua os métodos virtuais On*Event e On\*PreviewEvent correspondentes. Para obter mais informações, consulte [Manipulação de classes de eventos roteados por classes base de controle](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementando operações do tipo "arrastar e soltar"  
 Um elemento de interface do usuário pode ser uma origem do arrasto, um destino de soltar ou ambos. Para implementar uma operação básica do tipo "arrastar e soltar", um código é escrito para iniciar a operação do tipo "arrastar e soltar" e processar os dados soltos. É possível melhorar essa experiência de "arrastar e soltar" manipulando eventos opcionais das operações do tipo "arrastar e soltar".  
  
 Para implementar uma operação básica do tipo "arrastar e soltar", você realizará as seguintes tarefas:  
  
- Identificar o elemento que será uma origem do arrasto. Uma origem do arrasto pode ser um <xref:System.Windows.UIElement> ou um <xref:System.Windows.ContentElement>.  
  
- Criar um manipulador de eventos na origem do arrasto que iniciará a operação do tipo "arrastar e soltar". O evento é geralmente o <xref:System.Windows.UIElement.MouseMove> eventos.  
  
- No manipulador de eventos do código-fonte de arrastar, chame o <xref:System.Windows.DragDrop.DoDragDrop%2A> método para iniciar a operação de arrastar e soltar. No <xref:System.Windows.DragDrop.DoDragDrop%2A> chamar, especifique a origem do arrasto, os dados a serem transferidos e os efeitos permitidos.  
  
- Identificar o elemento que será um destino de soltar. Um destino de soltar pode ser <xref:System.Windows.UIElement> ou um <xref:System.Windows.ContentElement>.  
  
- No destino de soltar, defina as <xref:System.Windows.UIElement.AllowDrop%2A> propriedade para `true`.  
  
- No destino de soltar, crie um <xref:System.Windows.DragDrop.Drop> manipulador de eventos para processar os dados soltos.  
  
- No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, extrair os dados de <xref:System.Windows.DragEventArgs> usando o <xref:System.Windows.DataObject.GetDataPresent%2A> e <xref:System.Windows.DataObject.GetData%2A> métodos.  
  
- No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, use os dados para executar a operação de arrastar e soltar desejada.  
  
 Você pode aprimorar sua implementação de arrastar e soltar, criando um personalizado <xref:System.Windows.DataObject> e pela manipulação opcional arraste a origem e soltar eventos de destino, conforme mostrado nas seguintes tarefas:  
  
- Para transferir dados personalizados ou vários itens de dados, criar uma <xref:System.Windows.DataObject> para passar para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método.  
  
- Para executar ações adicionais durante uma operação de arrastar, lidar com o <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver>, e <xref:System.Windows.DragDrop.DragLeave> eventos no destino de soltar.  
  
- Para alterar a aparência do ponteiro do mouse, manipule o <xref:System.Windows.DragDrop.GiveFeedback> eventos na origem do arrasto.  
  
- Para alterar como a operação de arrastar e soltar é cancelada, manipule o <xref:System.Windows.DragDrop.QueryContinueDrag> eventos na origem do arrasto.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Exemplo de operação do tipo "arrastar e soltar"  
 Esta seção descreve como implementar o arrastar e soltar para um <xref:System.Windows.Shapes.Ellipse> elemento. O <xref:System.Windows.Shapes.Ellipse> é uma origem do arrasto e um destino de soltar. Os dados transferidos são a representação de cadeia de caracteres da elipse <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade. O XAML a seguir mostra o <xref:System.Windows.Shapes.Ellipse> elemento e os eventos relacionados de arrastar e soltar que ele manipula. Para obter etapas completas sobre como implementar o arrastar e soltar, consulte [passo a passo: Habilitando arrastar e soltar em um controle de usuário](walkthrough-enabling-drag-and-drop-on-a-user-control.md).  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Habilitando um elemento a ser uma origem do arrasto  
 Um objeto que é uma origem do arrasto é responsável por:  
  
- Identificar quando ocorre uma operação de arrastar.  
  
- Iniciar a operação do tipo "arrastar e soltar".  
  
- Identificar os dados a serem transferidos.  
  
- Especificar os efeitos que a operação do tipo "arrastar e soltar" tem permissão para ter sobre os dados transferidos.  
  
 A origem do arrasto também pode fornecer comentários ao usuário sobre as ações permitidas (mover, copiar, nenhuma) e pode cancelar a operação do tipo "arrastar e soltar" de acordo com a entrada adicional do usuário, como pressionar a tecla ESC durante a operação de arrastar.  
  
 É responsabilidade do seu aplicativo para determinar quando ocorre uma operação de arrastar e, em seguida, a operação de iniciar o arrastar e soltar chamando o <xref:System.Windows.DragDrop.DoDragDrop%2A> método. Normalmente, isso é quando um <xref:System.Windows.UIElement.MouseMove> evento ocorre sobre o elemento a ser arrastado enquanto um botão do mouse é pressionado. O exemplo a seguir mostra como iniciar uma operação de arrastar e soltar do <xref:System.Windows.UIElement.MouseMove> manipulador de eventos de um <xref:System.Windows.Shapes.Ellipse> elemento para torná-lo uma origem do arrasto. Os dados transferidos são a representação de cadeia de caracteres da elipse <xref:System.Windows.Shapes.Shape.Fill%2A> propriedade.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Dentro do <xref:System.Windows.UIElement.MouseMove> manipulador de eventos, chame o <xref:System.Windows.DragDrop.DoDragDrop%2A> método para iniciar a operação de arrastar e soltar. O <xref:System.Windows.DragDrop.DoDragDrop%2A> método assume três parâmetros:  
  
- `dragSource` – Uma referência ao objeto de dependência que é a origem dos dados transferidos; Isso normalmente é a origem do <xref:System.Windows.UIElement.MouseMove> eventos.  
  
- `data` -Um objeto que contém os dados transferidos, encapsulados em um <xref:System.Windows.DataObject>.  
  
- `allowedEffects` -Pode ser o <xref:System.Windows.DragDropEffects> valores de enumeração que especifica os efeitos permitidos da operação de arrastar e soltar.  
  
 Qualquer objeto serializável pode ser passado no parâmetro `data`. Se os dados não estiverem encapsulados em um <xref:System.Windows.DataObject>, ele será automaticamente encapsulado em um novo <xref:System.Windows.DataObject>. Para passar vários itens de dados, você deve criar o <xref:System.Windows.DataObject> por conta própria e passá-lo para o <xref:System.Windows.DragDrop.DoDragDrop%2A> método. Para obter mais informações, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 O parâmetro `allowedEffects` é usado para especificar o que a origem do arrasto permitirá que o destino de soltar faça com os dados transferidos. Os valores comuns para uma origem do arrasto são <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move>, e <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
>  O destino de soltar também pode especificar quais efeitos ele pretender ter em resposta aos dados soltos. Por exemplo, se o destino de soltar não reconhecer o tipo de dados a ser removido, ele poderá recusar os dados configurando seus efeitos permitidos para <xref:System.Windows.DragDropEffects.None>. Normalmente, ele faz isso seu <xref:System.Windows.DragDrop.DragOver> manipulador de eventos.  
  
 Uma origem do arrasto pode manipular, opcionalmente, o <xref:System.Windows.DragDrop.GiveFeedback> e <xref:System.Windows.DragDrop.QueryContinueDrag> eventos. Esses eventos têm manipuladores padrão que são usados, a menos que você marque os eventos como manipulados. Normalmente, você ignorará esses eventos, a menos que tenha uma necessidade específica de alterar seu comportamento padrão.  
  
 O <xref:System.Windows.DragDrop.GiveFeedback> evento é acionado continuamente enquanto a origem do arrasto está sendo arrastada. O manipulador padrão para esse evento verifica se a origem do arrasto está sobre um destino de soltar válido. Se estiver, ela verificará os efeitos permitidos do destino de soltar. Em seguida, ela fornece comentários ao usuário final sobre os efeitos de soltar permitidos. Geralmente, isso é feito com a alteração do cursor do mouse para um cursor do tipo não soltar, copiar ou mover. Você só deverá manipular esse evento se precisar usar cursores personalizados para fornecer comentários ao usuário. Se você manipular esse evento, lembre-se de marcá-lo como manipulado para que o manipulador padrão não substitua o manipulador.  
  
 O <xref:System.Windows.DragDrop.QueryContinueDrag> evento é acionado continuamente enquanto a origem do arrasto está sendo arrastada. Você pode manipular esse evento para determinar qual ação encerra a operação do tipo "arrastar e soltar", de acordo com o estado das teclas ESC, SHIFT, CTRL e ALT, bem como o estado dos botões do mouse. O manipulador padrão desse evento cancela a operação do tipo "arrastar e soltar" se a tecla ESC é pressionada e solta os dados se o botão do mouse é liberado.  
  
> [!CAUTION]
>  Esses eventos são acionados continuamente durante a operação do tipo "arrastar e soltar". Portanto, você deve evitar tarefas com uso intensivo de recursos nos manipuladores de eventos.  Por exemplo, usar um cursor em cache em vez de criar um novo cursor sempre que o <xref:System.Windows.DragDrop.GiveFeedback> é gerado.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Habilitando um elemento a ser um destino de soltar  
 Um objeto que é um destino de soltar é responsável por:  
  
- Especificar se ele é um destino de soltar válido.  
  
- Responder à origem do arrasto quando ele é arrastado para o destino.  
  
- Verificar se os dados transferidos estão em um formato que pode ser recebido.  
  
- Processar os dados soltos.  
  
 Para especificar que um elemento é um destino de soltar, defina suas <xref:System.Windows.UIElement.AllowDrop%2A> propriedade para `true`. Em seguida, os eventos de destino de soltar serão acionados no elemento, para que você possa manipulá-los. Durante uma operação do tipo "arrastar e soltar", ocorre a seguinte sequência de eventos no destino de soltar:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> ou <xref:System.Windows.DragDrop.Drop>  
  
 O <xref:System.Windows.DragDrop.DragEnter> evento ocorre quando os dados são arrastados para limites do destino de soltar. Normalmente, esse evento é manipulado para fornecer uma visualização dos efeitos da operação do tipo "arrastar e soltar", se apropriado para o aplicativo. Não defina a <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> propriedade no <xref:System.Windows.DragDrop.DragEnter> evento, como ele será substituído no <xref:System.Windows.DragDrop.DragOver> eventos.  
  
 A exemplo a seguir mostra a <xref:System.Windows.DragDrop.DragEnter> manipulador de eventos para um <xref:System.Windows.Shapes.Ellipse> elemento. Esse código visualiza os efeitos da operação de arrastar e soltar, salvando atual <xref:System.Windows.Shapes.Shape.Fill%2A> pincel. Ele usa o <xref:System.Windows.DataObject.GetDataPresent%2A> método para verificar se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Se assim, os dados são extraídos usando o <xref:System.Windows.DataObject.GetData%2A> método. Em seguida, ele será convertido em um <xref:System.Windows.Media.Brush> e aplicados à elipse. A alteração é revertida no <xref:System.Windows.DragDrop.DragLeave> manipulador de eventos. Se os dados não podem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação é executada.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 O <xref:System.Windows.DragDrop.DragOver> evento ocorre continuamente enquanto os dados são arrastados sobre o destino de soltar. Esse evento é emparelhado com o <xref:System.Windows.DragDrop.GiveFeedback> eventos na origem do arrasto. No <xref:System.Windows.DragDrop.DragOver> manipulador de eventos, normalmente, você usa o <xref:System.Windows.DataObject.GetDataPresent%2A> e <xref:System.Windows.DataObject.GetData%2A> métodos para verificar se os dados transferidos estão em um formato que o destino de soltar pode processar. Também é possível verificar se teclas modificadoras são pressionadas, o que geralmente indica se o usuário pretende executar uma ação de mover ou copiar. Depois que essas verificações são executadas, você definir o <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> terá o efeito de soltar os dados de origem de propriedade para notificar a operação de arrastar. A origem do arrasto recebe essas informações no <xref:System.Windows.DragDrop.GiveFeedback> args de evento e pode definir um cursor apropriado para fornecer comentários ao usuário.  
  
 A exemplo a seguir mostra a <xref:System.Windows.DragDrop.DragOver> manipulador de eventos para um <xref:System.Windows.Shapes.Ellipse> elemento. Esse código verifica se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Se assim, ele define o <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> propriedade para <xref:System.Windows.DragDropEffects.Copy>. Isso indica à origem do arrasto que os dados podem ser copiados para a elipse. Se os dados não podem ser convertidos em um <xref:System.Windows.Media.Brush>, o <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> estiver definida como <xref:System.Windows.DragDropEffects.None>. Isso indica à origem do arrasto que a elipse não é um destino de soltar válido para os dados.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 O <xref:System.Windows.DragDrop.DragLeave> evento ocorre quando os dados são arrastados fora os limites do destino sem serem soltos. Você manipular esse evento para desfazer qualquer coisa que você fez no <xref:System.Windows.DragDrop.DragEnter> manipulador de eventos.  
  
 A exemplo a seguir mostra a <xref:System.Windows.DragDrop.DragLeave> manipulador de eventos para um <xref:System.Windows.Shapes.Ellipse> elemento. Esse código desfaz a visualização executada na <xref:System.Windows.DragDrop.DragEnter> manipulador de eventos, aplicando o salvo <xref:System.Windows.Media.Brush> à elipse.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 O <xref:System.Windows.DragDrop.Drop> evento ocorre quando os dados são soltos no destino de soltar; por padrão, isso ocorre quando o botão do mouse é liberado. No <xref:System.Windows.DragDrop.Drop> manipulador de eventos, use o <xref:System.Windows.DataObject.GetData%2A> método para extrair os dados transferidos a <xref:System.Windows.DataObject> e executar qualquer processamento de dados que seu aplicativo requer. O <xref:System.Windows.DragDrop.Drop> evento encerra a operação de arrastar e soltar.  
  
 A exemplo a seguir mostra a <xref:System.Windows.DragDrop.Drop> manipulador de eventos para um <xref:System.Windows.Shapes.Ellipse> elemento. Esse código aplica os efeitos da operação de arrastar e soltar e é semelhante ao código no <xref:System.Windows.DragDrop.DragEnter> manipulador de eventos. Ele verifica se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Nesse caso, o <xref:System.Windows.Media.Brush> é aplicada à elipse. Se os dados não podem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação é executada.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Clipboard>
- [Passo a passo: Habilitando arrastar e soltar em um controle de usuário](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [Tópicos de instruções](drag-and-drop-how-to-topics.md)
- [Arrastar e soltar](drag-and-drop.md)
