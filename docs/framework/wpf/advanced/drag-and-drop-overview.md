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
ms.openlocfilehash: 72dc443e5653b9871c3f67b003bd1af0536d5993
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291481"
---
# <a name="drag-and-drop-overview"></a>Visão geral de arrastar e soltar
Este tópico fornece uma visão geral do suporte ao recurso do tipo "arrastar e soltar" em aplicativos do [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Normalmente, o recurso do tipo "arrastar e soltar" se refere a um método de transferência de dados que envolve o uso de um mouse (ou algum outro dispositivo apontador) para selecionar um ou mais objetos, arrastá-los sobre um destino de soltar desejado na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] e soltá-los.  

<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>Suporte ao recurso do tipo "arrastar e soltar" no WPF  
 Normalmente, as operações do tipo "arrastar e soltar" envolvem duas partes: uma origem do arrasto da qual o objeto arrastado se origina e um destino de soltar que recebe o objeto solto.  A origem do arrasto e o destino de soltar podem ser elementos de interface do usuário no mesmo ou em outro aplicativo.  
  
 O tipo e o número de objetos que podem ser manipulados com o recurso do tipo "arrastar e soltar" é completamente arbitrário. Por exemplo, arquivos, pastas e seleções de conteúdo são alguns dos objetos mais comuns manipulados por meio de operações do tipo "arrastar e soltar".  
  
 As ações específicas realizadas durante uma operação do tipo "arrastar e soltar" são específicas ao aplicativo e, frequentemente, determinadas pelo contexto.  Por exemplo, arrastar uma seleção de arquivos de uma pasta para outra no mesmo dispositivo de armazenamento move os arquivos por padrão, ao passo que arrastar arquivos de um compartilhamento UNC (Convenção de nomenclatura universal) para uma pasta local copia os arquivos por padrão.  
  
 As funcionalidades do tipo "arrastar e soltar" fornecidas pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] foram projetadas para serem altamente flexíveis e personalizáveis, a fim de dar suporte a uma ampla variedade de cenários de operações do tipo "arrastar e soltar".  As operações do tipo "arrastar e soltar" dão suporte à manipulação de objetos em um único aplicativo ou entre diferentes aplicativos. Também há suporte completo para arrastar e soltar entre aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e outros aplicativos do Windows.  
  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qualquer <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> pode participar do recurso de arrastar e soltar. Os eventos e os métodos necessários para operações de arrastar e soltar são definidos na classe <xref:System.Windows.DragDrop>. As classes <xref:System.Windows.UIElement> e <xref:System.Windows.ContentElement> contêm aliases para os eventos anexados <xref:System.Windows.DragDrop> para que os eventos apareçam na lista Membros da classe quando um <xref:System.Windows.UIElement> ou <xref:System.Windows.ContentElement> é herdado como um elemento base. Os manipuladores de eventos anexados a esses eventos são anexados ao evento de anexação <xref:System.Windows.DragDrop> subjacente e recebem a mesma instância de dados de evento. Para saber mais, confira o evento <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Operações do tipo "arrastar e soltar" OLE não funcionarão se você estiver na zona da Internet.  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>Transferência de dados  
 Arrastar e soltar faz parte da área de transferência de dados mais geral. A transferência de dados inclui operações do tipo "arrastar e soltar" e copiar e colar. Uma operação do tipo "arrastar e soltar" é análoga a uma operação de copiar e colar ou de recortar e colar, que é usada para transferir dados de um objeto ou aplicativo para outro usando a área de transferência do sistema. Os dois tipos de operações exigem:  
  
- Um objeto de origem que fornece os dados.  
  
- Uma maneira de armazenar temporariamente os dados transferidos.  
  
- Um objeto de destino que recebe os dados.  
  
 Em uma operação copiar e colar, a área de transferência do sistema é usada para armazenar temporariamente os dados transferidos; em uma operação de arrastar e soltar, um <xref:System.Windows.DataObject> é usado para armazenar os dados. Conceitualmente, um objeto de dados consiste em um ou mais pares de um <xref:System.Object> que contém os dados reais e um identificador de formato de dados correspondente.  
  
 A fonte de arrastar inicia uma operação de arrastar e soltar chamando o método estático <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> e passando os dados transferidos para ele. O método <xref:System.Windows.DragDrop.DoDragDrop%2A> encapsulará automaticamente os dados em um <xref:System.Windows.DataObject>, se necessário. Para obter maior controle sobre o formato de dados, você pode encapsular os dados em um <xref:System.Windows.DataObject> antes de passá-los para o método <xref:System.Windows.DragDrop.DoDragDrop%2A>. O destino de soltura é responsável por extrair os dados do <xref:System.Windows.DataObject>. Para obter mais informações sobre como trabalhar com objetos de dados, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 A origem e o destino de uma operação do tipo "arrastar e soltar" são elementos de interface do usuário; no entanto, os dados que realmente são transferidos, normalmente, não têm uma representação visual. É possível escrever um código para fornecer uma representação visual dos dados que são arrastados, assim como ocorre ao arrastar arquivos no Windows Explorer. Por padrão, comentários são fornecidos ao usuário com a alteração do cursor para representar o efeito que a operação do tipo "arrastar e soltar" terá sobre os dados, por exemplo, se os dados serão movidos ou copiados.  
  
### <a name="drag-and-drop-effects"></a>Efeitos das operações do tipo "arrastar e soltar"  
 Operações do tipo "arrastar e soltar" podem ter efeitos diferentes nos dados transferidos. Por exemplo, é possível copiar os dados ou movê-los. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] define uma enumeração de <xref:System.Windows.DragDropEffects> que você pode usar para especificar o efeito de uma operação de arrastar e soltar. Na fonte de arrastar, você pode especificar os efeitos que a origem permitirá no método <xref:System.Windows.DragDrop.DoDragDrop%2A>. No destino de soltar, você pode especificar o efeito que o destino pretende na propriedade <xref:System.Windows.DragEventArgs.Effects%2A> da classe <xref:System.Windows.DragEventArgs>. Quando o destino de soltura especifica seu efeito pretendido no evento <xref:System.Windows.DragDrop.DragOver>, essas informações são passadas de volta para a fonte de arrastar no evento <xref:System.Windows.DragDrop.GiveFeedback>. A origem do arrasto usa essas informações para informar ao usuário o efeito que o destino de soltar pretende ter sobre os dados. Quando os dados são descartados, o destino de soltura especifica seu efeito real no evento <xref:System.Windows.DragDrop.Drop>. Essas informações são passadas de volta para a fonte de arrastar como o valor de retorno do método <xref:System.Windows.DragDrop.DoDragDrop%2A>. Se o destino de soltar retornar um efeito que não está na lista `allowedEffects` da origem do arrasto, a operação do tipo "arrastar e soltar" será cancelada sem nenhuma transferência de dados.  
  
 É importante lembrar que, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], os valores de <xref:System.Windows.DragDropEffects> são usados apenas para fornecer comunicação entre a origem de arrastar e o destino de soltar em relação aos efeitos da operação de arrastar e soltar. O efeito real da operação do tipo "arrastar e soltar" depende da escrita do código apropriado no aplicativo.  
  
 Por exemplo, o destino de soltar pode especificar que o efeito de soltar dados nele é mover os dados. No entanto, para mover os dados, ele deve ser adicionado ao elemento de destino e removido do elemento de origem. O elemento de origem pode indicar que ele permite a movimentação dos dados, mas se você não fornecer o código para remover os dados do elemento de origem, o resultado final será que os dados serão copiados e não movidos.  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>Eventos das operações do tipo "arrastar e soltar"  
 As operações do tipo "arrastar e soltar" dão suporte a um modelo controlado por evento.  A origem do arrasto e o destino de soltar usam um conjunto padrão de eventos para manipular operações do tipo "arrastar e soltar".  As tabelas a seguir resumem os eventos padrão das operações do tipo "arrastar e soltar". Esses são eventos anexados na classe <xref:System.Windows.DragDrop>. Para obter mais informações sobre eventos anexados, consulte [Visão geral dos eventos anexados](attached-events-overview.md).  
  
### <a name="drag-source-events"></a>Eventos de origem do arrasto  
  
|evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|Esse evento ocorre continuamente durante uma operação do tipo "arrastar e soltar" e permite que a origem de soltar forneça informações de comentários ao usuário. Geralmente, esses comentários são fornecidos com a alteração da aparência do ponteiro do mouse para indicar os efeitos permitidos pelo destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|Esse evento ocorre quando há uma alteração nos estados do teclado ou do botão do mouse durante uma do tipo "arrastar e soltar" e permite que a origem de soltar cancele a operação do tipo "arrastar e soltar", dependendo dos estados da tecla e do botão. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|Versão de túnel do <xref:System.Windows.DragDrop.GiveFeedback>.|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|Versão de túnel do <xref:System.Windows.DragDrop.QueryContinueDrag>.|  
  
### <a name="drop-target-events"></a>Eventos de destino de soltar  
  
|evento|Resumo|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|Esse evento ocorre quando um objeto é arrastado para os limites do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragLeave>|Esse evento ocorre quando um objeto é arrastado para fora dos limites do destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.DragOver>|Esse evento ocorre continuamente enquanto um objeto é arrastado (movido) dentro do limite do destino de soltar. Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.Drop>|Esse evento ocorre quando um objeto é solto no destino de soltar.  Esse é um evento de propagação.|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|Versão de túnel do <xref:System.Windows.DragDrop.DragEnter>.|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|Versão de túnel do <xref:System.Windows.DragDrop.DragLeave>.|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|Versão de túnel do <xref:System.Windows.DragDrop.DragOver>.|  
|<xref:System.Windows.DragDrop.PreviewDrop>|Versão de túnel do <xref:System.Windows.DragDrop.Drop>.|  
  
 Para manipular eventos das operações do tipo "arrastar e soltar" em instâncias de um objeto, adicione manipuladores para os eventos listados nas tabelas anteriores. Para manipular eventos das operações do tipo "arrastar e soltar" no nível de classe, substitua os métodos virtuais On*Event e On\*PreviewEvent correspondentes. Para obter mais informações, consulte [Manipulação de classes de eventos roteados por classes base de controle](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events).  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>Implementando operações do tipo "arrastar e soltar"  
 Um elemento de interface do usuário pode ser uma origem do arrasto, um destino de soltar ou ambos. Para implementar uma operação básica do tipo "arrastar e soltar", um código é escrito para iniciar a operação do tipo "arrastar e soltar" e processar os dados soltos. É possível melhorar essa experiência de "arrastar e soltar" manipulando eventos opcionais das operações do tipo "arrastar e soltar".  
  
 Para implementar uma operação básica do tipo "arrastar e soltar", você realizará as seguintes tarefas:  
  
- Identificar o elemento que será uma origem do arrasto. Uma fonte de arrastar pode ser uma <xref:System.Windows.UIElement> ou uma <xref:System.Windows.ContentElement>.  
  
- Criar um manipulador de eventos na origem do arrasto que iniciará a operação do tipo "arrastar e soltar". O evento é normalmente o evento <xref:System.Windows.UIElement.MouseMove>.  
  
- No manipulador de eventos de arrastar fonte, chame o método <xref:System.Windows.DragDrop.DoDragDrop%2A> para iniciar a operação de arrastar e soltar. Na chamada <xref:System.Windows.DragDrop.DoDragDrop%2A>, especifique a fonte de arrastar, os dados a serem transferidos e os efeitos permitidos.  
  
- Identificar o elemento que será um destino de soltar. Um destino de soltura pode ser <xref:System.Windows.UIElement> ou um <xref:System.Windows.ContentElement>.  
  
- No destino de soltura, defina a propriedade <xref:System.Windows.UIElement.AllowDrop%2A> como `true`.  
  
- No destino de soltar, crie um manipulador de eventos <xref:System.Windows.DragDrop.Drop> para processar os dados eliminados.  
  
- No manipulador de eventos <xref:System.Windows.DragDrop.Drop>, extraia os dados do <xref:System.Windows.DragEventArgs> usando os métodos <xref:System.Windows.DataObject.GetDataPresent%2A> e <xref:System.Windows.DataObject.GetData%2A>.  
  
- No manipulador de eventos <xref:System.Windows.DragDrop.Drop>, use os dados para executar a operação de arrastar e soltar desejada.  
  
 Você pode aprimorar a implementação do tipo "arrastar e soltar" criando um <xref:System.Windows.DataObject> personalizado e manipulando eventos de destino arrastar fonte e soltar opcionais, conforme mostrado nas seguintes tarefas:  
  
- Para transferir dados personalizados ou vários itens de dados, crie um <xref:System.Windows.DataObject> para passar para o método <xref:System.Windows.DragDrop.DoDragDrop%2A>.  
  
- Para executar ações adicionais durante um arrastar, manipule os eventos <xref:System.Windows.DragDrop.DragEnter>, <xref:System.Windows.DragDrop.DragOver> e <xref:System.Windows.DragDrop.DragLeave> no destino de soltar.  
  
- Para alterar a aparência do ponteiro do mouse, manipule o evento <xref:System.Windows.DragDrop.GiveFeedback> na fonte de arrastar.  
  
- Para alterar a forma como a operação de arrastar e soltar é cancelada, manipule o evento <xref:System.Windows.DragDrop.QueryContinueDrag> na fonte de arrastar.  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>Exemplo de operação do tipo "arrastar e soltar"  
 Esta seção descreve como implementar o recurso de arrastar e soltar para um elemento <xref:System.Windows.Shapes.Ellipse>. O <xref:System.Windows.Shapes.Ellipse> é uma origem de arrastar e um destino de soltar. Os dados transferidos são a representação da cadeia de caracteres da propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> da elipse. O XAML a seguir mostra o elemento <xref:System.Windows.Shapes.Ellipse> e os eventos relacionados ao recurso de arrastar e soltar que ele manipula. Para obter as etapas completas sobre como implementar o recurso de arrastar e soltar, consulte [Walkthrough: Habilitando o recurso de arrastar e soltar em um controle de usuário @ no__t-0.  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>Habilitando um elemento a ser uma origem do arrasto  
 Um objeto que é uma origem do arrasto é responsável por:  
  
- Identificar quando ocorre uma operação de arrastar.  
  
- Iniciar a operação do tipo "arrastar e soltar".  
  
- Identificar os dados a serem transferidos.  
  
- Especificar os efeitos que a operação do tipo "arrastar e soltar" tem permissão para ter sobre os dados transferidos.  
  
 A origem do arrasto também pode fornecer comentários ao usuário sobre as ações permitidas (mover, copiar, nenhuma) e pode cancelar a operação do tipo "arrastar e soltar" de acordo com a entrada adicional do usuário, como pressionar a tecla ESC durante a operação de arrastar.  
  
 É responsabilidade do seu aplicativo determinar quando um arrasto ocorre e, em seguida, iniciar a operação de arrastar e soltar chamando o método <xref:System.Windows.DragDrop.DoDragDrop%2A>. Normalmente, é quando um evento <xref:System.Windows.UIElement.MouseMove> ocorre sobre o elemento a ser arrastado enquanto um botão do mouse é pressionado. O exemplo a seguir mostra como iniciar uma operação de arrastar e soltar do manipulador de eventos <xref:System.Windows.UIElement.MouseMove> de um elemento <xref:System.Windows.Shapes.Ellipse> para torná-lo uma fonte de arrastar. Os dados transferidos são a representação da cadeia de caracteres da propriedade <xref:System.Windows.Shapes.Shape.Fill%2A> da elipse.  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 Dentro do manipulador de eventos <xref:System.Windows.UIElement.MouseMove>, chame o método <xref:System.Windows.DragDrop.DoDragDrop%2A> para iniciar a operação de arrastar e soltar. O método <xref:System.Windows.DragDrop.DoDragDrop%2A> usa três parâmetros:  
  
- `dragSource` – uma referência ao objeto de dependência que é a origem dos dados transferidos; Normalmente, essa é a origem do evento <xref:System.Windows.UIElement.MouseMove>.  
  
- `data`-um objeto que contém os dados transferidos, encapsulados em um <xref:System.Windows.DataObject>.  
  
- `allowedEffects`-um dos valores de enumeração de <xref:System.Windows.DragDropEffects> que especifica os efeitos permitidos da operação de arrastar e soltar.  
  
 Qualquer objeto serializável pode ser passado no parâmetro `data`. Se os dados ainda não estiverem encapsulados em um <xref:System.Windows.DataObject>, eles serão automaticamente encapsulados em um novo <xref:System.Windows.DataObject>. Para passar vários itens de dados, você deve criar o <xref:System.Windows.DataObject> por conta própria e passá-lo para o método <xref:System.Windows.DragDrop.DoDragDrop%2A>. Para obter mais informações, consulte [Dados e objetos de dados](data-and-data-objects.md).  
  
 O parâmetro `allowedEffects` é usado para especificar o que a origem do arrasto permitirá que o destino de soltar faça com os dados transferidos. Os valores comuns para uma fonte de arrastar são <xref:System.Windows.DragDropEffects.Copy>, <xref:System.Windows.DragDropEffects.Move> e <xref:System.Windows.DragDropEffects.All>.  
  
> [!NOTE]
> O destino de soltar também pode especificar quais efeitos ele pretender ter em resposta aos dados soltos. Por exemplo, se o destino de soltura não reconhecer o tipo de dados a ser removido, ele poderá recusar os dados definindo seus efeitos permitidos para <xref:System.Windows.DragDropEffects.None>. Normalmente, ele faz isso em seu manipulador de eventos <xref:System.Windows.DragDrop.DragOver>.  
  
 Uma fonte de arrastar pode, opcionalmente, manipular os eventos <xref:System.Windows.DragDrop.GiveFeedback> e <xref:System.Windows.DragDrop.QueryContinueDrag>. Esses eventos têm manipuladores padrão que são usados, a menos que você marque os eventos como manipulados. Normalmente, você ignorará esses eventos, a menos que tenha uma necessidade específica de alterar seu comportamento padrão.  
  
 O evento <xref:System.Windows.DragDrop.GiveFeedback> é gerado continuamente enquanto a origem do arrasto está sendo arrastada. O manipulador padrão para esse evento verifica se a origem do arrasto está sobre um destino de soltar válido. Se estiver, ela verificará os efeitos permitidos do destino de soltar. Em seguida, ela fornece comentários ao usuário final sobre os efeitos de soltar permitidos. Geralmente, isso é feito com a alteração do cursor do mouse para um cursor do tipo não soltar, copiar ou mover. Você só deverá manipular esse evento se precisar usar cursores personalizados para fornecer comentários ao usuário. Se você manipular esse evento, lembre-se de marcá-lo como manipulado para que o manipulador padrão não substitua o manipulador.  
  
 O evento <xref:System.Windows.DragDrop.QueryContinueDrag> é gerado continuamente enquanto a origem do arrasto está sendo arrastada. Você pode manipular esse evento para determinar qual ação encerra a operação do tipo "arrastar e soltar", de acordo com o estado das teclas ESC, SHIFT, CTRL e ALT, bem como o estado dos botões do mouse. O manipulador padrão desse evento cancela a operação do tipo "arrastar e soltar" se a tecla ESC é pressionada e solta os dados se o botão do mouse é liberado.  
  
> [!CAUTION]
> Esses eventos são acionados continuamente durante a operação do tipo "arrastar e soltar". Portanto, você deve evitar tarefas com uso intensivo de recursos nos manipuladores de eventos.  Por exemplo, use um cursor em cache em vez de criar um novo cursor a cada vez que o evento <xref:System.Windows.DragDrop.GiveFeedback> for gerado.  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>Habilitando um elemento a ser um destino de soltar  
 Um objeto que é um destino de soltar é responsável por:  
  
- Especificar se ele é um destino de soltar válido.  
  
- Responder à origem do arrasto quando ele é arrastado para o destino.  
  
- Verificar se os dados transferidos estão em um formato que pode ser recebido.  
  
- Processar os dados soltos.  
  
 Para especificar que um elemento é um destino de soltar, defina sua propriedade <xref:System.Windows.UIElement.AllowDrop%2A> como `true`. Em seguida, os eventos de destino de soltar serão acionados no elemento, para que você possa manipulá-los. Durante uma operação do tipo "arrastar e soltar", ocorre a seguinte sequência de eventos no destino de soltar:  
  
1. <xref:System.Windows.DragDrop.DragEnter>  
  
2. <xref:System.Windows.DragDrop.DragOver>  
  
3. <xref:System.Windows.DragDrop.DragLeave> ou <xref:System.Windows.DragDrop.Drop>  
  
 O evento <xref:System.Windows.DragDrop.DragEnter> ocorre quando os dados são arrastados para o limite de destino da remoção. Normalmente, esse evento é manipulado para fornecer uma visualização dos efeitos da operação do tipo "arrastar e soltar", se apropriado para o aplicativo. Não defina a propriedade <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> no evento <xref:System.Windows.DragDrop.DragEnter>, pois ela será substituída no evento <xref:System.Windows.DragDrop.DragOver>.  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.DragDrop.DragEnter> para um elemento <xref:System.Windows.Shapes.Ellipse>. Esse código visualiza os efeitos da operação de arrastar e soltar salvando o pincel <xref:System.Windows.Shapes.Shape.Fill%2A> atual. Em seguida, ele usa o método <xref:System.Windows.DataObject.GetDataPresent%2A> para verificar se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Nesse caso, os dados são extraídos usando o método <xref:System.Windows.DataObject.GetData%2A>. Em seguida, ele é convertido em um <xref:System.Windows.Media.Brush> e aplicado à elipse. A alteração é revertida no manipulador de eventos <xref:System.Windows.DragDrop.DragLeave>. Se os dados não puderem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação será executada.  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 O evento <xref:System.Windows.DragDrop.DragOver> ocorre continuamente enquanto os dados são arrastados sobre o destino de soltura. Esse evento é emparelhado com o evento <xref:System.Windows.DragDrop.GiveFeedback> na fonte de arrastar. No manipulador de eventos <xref:System.Windows.DragDrop.DragOver>, você normalmente usa os métodos <xref:System.Windows.DataObject.GetDataPresent%2A> e <xref:System.Windows.DataObject.GetData%2A> para verificar se os dados transferidos estão em um formato que o destino de soltar pode processar. Também é possível verificar se teclas modificadoras são pressionadas, o que geralmente indica se o usuário pretende executar uma ação de mover ou copiar. Depois que essas verificações forem executadas, você definirá a propriedade <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> para notificar a fonte de arrastar que o efeito descartar os dados terá. A origem de arrastar recebe essas informações nos args de evento <xref:System.Windows.DragDrop.GiveFeedback> e pode definir um cursor apropriado para fornecer comentários ao usuário.  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.DragDrop.DragOver> para um elemento <xref:System.Windows.Shapes.Ellipse>. Esse código verifica se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Nesse caso, ele define a propriedade <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> como <xref:System.Windows.DragDropEffects.Copy>. Isso indica à origem do arrasto que os dados podem ser copiados para a elipse. Se os dados não puderem ser convertidos em um <xref:System.Windows.Media.Brush>, a propriedade <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> será definida como <xref:System.Windows.DragDropEffects.None>. Isso indica à origem do arrasto que a elipse não é um destino de soltar válido para os dados.  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 O evento <xref:System.Windows.DragDrop.DragLeave> ocorre quando os dados são arrastados para fora do limite do destino sem serem descartados. Você manipula esse evento para desfazer tudo o que fez no manipulador de eventos <xref:System.Windows.DragDrop.DragEnter>.  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.DragDrop.DragLeave> para um elemento <xref:System.Windows.Shapes.Ellipse>. Esse código desfaz a visualização realizada no manipulador de eventos <xref:System.Windows.DragDrop.DragEnter> aplicando o <xref:System.Windows.Media.Brush> salvo à elipse.  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 O evento <xref:System.Windows.DragDrop.Drop> ocorre quando os dados são descartados sobre o destino de soltura; Por padrão, isso acontece quando o botão do mouse é liberado. No manipulador de eventos <xref:System.Windows.DragDrop.Drop>, você usa o método <xref:System.Windows.DataObject.GetData%2A> para extrair os dados transferidos do <xref:System.Windows.DataObject> e executar qualquer processamento de dados que seu aplicativo requer. O evento <xref:System.Windows.DragDrop.Drop> termina a operação de arrastar e soltar.  
  
 O exemplo a seguir mostra o manipulador de eventos <xref:System.Windows.DragDrop.Drop> para um elemento <xref:System.Windows.Shapes.Ellipse>. Esse código aplica os efeitos da operação de arrastar e soltar e é semelhante ao código no manipulador de eventos <xref:System.Windows.DragDrop.DragEnter>. Ele verifica se o <xref:System.Windows.DataObject> que está sendo arrastado sobre a elipse contém dados de cadeia de caracteres que podem ser convertidos em um <xref:System.Windows.Media.Brush>. Nesse caso, o <xref:System.Windows.Media.Brush> é aplicado à elipse. Se os dados não puderem ser convertidos em um <xref:System.Windows.Media.Brush>, nenhuma ação será executada.  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Clipboard>
- [Passo a passo: Habilitando arrastar e soltar em um controle de usuário @ no__t-0
- [Tópicos de instruções](drag-and-drop-how-to-topics.md)
- [Arrastar e soltar](drag-and-drop.md)
