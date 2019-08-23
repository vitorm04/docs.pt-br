---
title: Como a entrada do teclado funciona
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 369c434f5443334ccb8b136ce50ff2d5db8ece01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963440"
---
# <a name="how-keyboard-input-works"></a>Como a entrada do teclado funciona
O Windows Forms processa a entrada do teclado ao gerar eventos de teclado em resposta às mensagens do Windows. A maioria dos aplicativos Windows Forms processa a entrada do teclado exclusivamente ao manipular eventos de teclado. No entanto, você precisa entender como as mensagens do teclado funcionam para que você possa implementar cenários mais avançados de entrada do teclado, como interceptar teclas antes que elas atinjam um controle. Este tópico descreve os tipos de dados da chave que o Windows Forms reconhece e fornece uma visão geral de como as mensagens do teclado são roteadas. Para obter informações sobre eventos de teclado, consulte [Usando eventos do teclado](using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Tipos de teclas  
 Windows Forms identifica a entrada de teclado como códigos de chave virtual que são representados <xref:System.Windows.Forms.Keys> pela enumeração bit-de bits. Com a <xref:System.Windows.Forms.Keys> enumeração, você pode combinar uma série de teclas pressionadas para resultar em um único valor. Esses valores correspondem aos valores que acompanham as mensagens WM_KEYDOWN e WM_SYSKEYDOWN do Windows. Você pode detectar a maioria dos pressionamentos de chave física <xref:System.Windows.Forms.Control.KeyDown> manipulando os eventos ou <xref:System.Windows.Forms.Control.KeyUp> . As chaves de caractere são um subconjunto da <xref:System.Windows.Forms.Keys> enumeração e correspondem aos valores que acompanham as mensagens WM_CHAR e WM_SYSCHAR do Windows. Se a combinação de teclas pressionadas resultar em um caractere, você poderá detectar o caractere manipulando <xref:System.Windows.Forms.Control.KeyPress> o evento. Como alternativa, você pode usar <xref:Microsoft.VisualBasic.Devices.Keyboard>, exposto por Visual Basic interface de programação, para descobrir quais chaves foram pressionadas e enviar chaves. Para obter mais informações, consulte [Acessando o teclado](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Ordem dos eventos do teclado  
 Conforme listado anteriormente, existem três eventos relacionados que podem ocorrer em um controle. A sequência a seguir mostra a ordem geral dos eventos:  
  
1. O usuário envia por push a chave "a", a chave é pré-processado, despachada e ocorre um <xref:System.Windows.Forms.Control.KeyDown> evento.  
  
2. O usuário mantém a chave "a", a chave é pré-processado, despachada e um <xref:System.Windows.Forms.Control.KeyPress> evento ocorre.  
  
     Esse evento ocorre várias vezes enquanto o usuário pressiona uma tecla.  
  
3. O usuário libera a chave "a", a chave é pré-processado, despachada e ocorre um <xref:System.Windows.Forms.Control.KeyUp> evento.  
  
## <a name="preprocessing-keys"></a>Pré-processamento das teclas  
 Assim como outras mensagens, as mensagens do teclado são <xref:System.Windows.Forms.Control.WndProc%2A> processadas no método de um formulário ou controle. No entanto, antes que as mensagens do <xref:System.Windows.Forms.Control.PreProcessMessage%2A> teclado sejam processadas, o método chama um ou mais métodos que podem ser substituídos para manipular chaves de caracteres especiais e chaves físicas. Você pode substituir esses métodos para detectar e filtrar certas teclas antes que as mensagens sejam processadas pelo controle. A tabela a seguir mostra a ação que está sendo executada e o método relacionado que ocorre, na ordem em que o método ocorre.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Pré-processamento de um evento KeyDown  
  
|Ação|Método relacionado|Observações|  
|------------|--------------------|-----------|  
|Verifique se há uma chave de comando como um acelerador ou um atalho de menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Este método processa uma chave de comando, que tem precedência sobre teclas regulares. Se esse método retornar `true`, a mensagem principal não será enviada e um evento de tecla não ocorrerá. Se retornar `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> será chamado`.`|  
|Verifique se há uma chave especial que requer pré-processamento ou uma chave de caractere normal que deva gerar um <xref:System.Windows.Forms.Control.KeyDown> evento e ser expedido para um controle.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Se o método retornar `true`, significa que o controle é um caractere regular e um <xref:System.Windows.Forms.Control.KeyDown> evento é gerado. Se `false` ,<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> for chamado. **Observação:**  Para garantir que um controle obtenha uma chave ou uma combinação de chaves, você pode <xref:System.Windows.Forms.Control.PreviewKeyDown> manipular o evento <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> e o <xref:System.Windows.Forms.PreviewKeyDownEventArgs> conjunto `true` de para para a chave ou as chaves desejadas.|  
|Verifique se há uma tecla de navegação (teclas ESC, TAB, Enter ou teclas de seta).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Este método processa uma tecla física que utiliza uma funcionalidade especial dentro do controle, como alternar o foco entre o controle e seu pai. Se o controle imediato não tratar a chave, o <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> será chamado no controle pai e assim por diante para o controle de nível superior na hierarquia. Se esse método retornar `true`, o pré-processamento estará completo e um evento de tecla não será gerado. Se ele retornar `false`, ocorrerá um <xref:System.Windows.Forms.Control.KeyDown> evento.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Pré-processamento de um evento KeyPress  
  
|Ação|Método relacionado|Observações|  
|------------|--------------------|-----------|  
|Verifique se a chave é um caractere normal que deve ser processado pelo controle|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Se o caractere for um caractere normal, esse método retornará `true`, o <xref:System.Windows.Forms.Control.KeyPress> evento será gerado e nenhum outro pré-processamento ocorrerá. Caso <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> contrário, será chamado.|  
|Verifique se o caractere é um mnemônico (como &OK em um botão)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Esse método, semelhante a <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, será chamado de hierarquia de controle. Se o controle for um controle de contêiner, ele verificará mnemônicos chamando <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> a si mesmo e seus controles filho. Se <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> retornar `true`, um<xref:System.Windows.Forms.Control.KeyPress> evento não ocorrerá.|  
  
## <a name="processing-keyboard-messages"></a>Processando mensagens do teclado  
 Depois que as mensagens do <xref:System.Windows.Forms.Control.WndProc%2A> teclado atingem o método de um formulário ou controle, elas são processadas por um conjunto de métodos que podem ser substituídos. Cada um desses métodos retorna um <xref:System.Boolean> valor que especifica se a mensagem do teclado foi processada e consumida pelo controle. Se um dos métodos retornar `true`, então a mensagem será considerada tratada e ela não será passada para a base ou pai do controle para processamento adicional. Caso contrário, a mensagem permanecerá na fila e poderá ser processada em outro método da base ou pai do controle. A tabela a seguir apresenta os métodos que processam mensagens do teclado.  
  
|Método|Observações|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Esse método processa todas as mensagens de teclado que são recebidas pelo <xref:System.Windows.Forms.Control.WndProc%2A> método do controle.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Esse método envia a mensagem do teclado para o pai do controle. Se <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> retornar `true`, nenhum evento de chave será gerado; caso contrário, será chamado.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Esse método gera os <xref:System.Windows.Forms.Control.KeyDown>eventos <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp> , conforme apropriado.|  
  
## <a name="overriding-keyboard-methods"></a>Substituindo métodos do teclado  
 Há vários métodos disponíveis para substituição quando uma mensagem do teclado é pré-processada e processada. No entanto, alguns métodos são opções muito melhores do que outros. A tabela a seguir mostra tarefas que você talvez queira realizar e a melhor maneira de substituir os métodos do teclado. Para obter mais informações sobre como substituir métodos, consulte [substituindo Propriedades e métodos em classes derivadas](../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Tarefa|Método|  
|----------|------------|  
|Interceptar uma chave de navegação e <xref:System.Windows.Forms.Control.KeyDown> gerar um evento. Por exemplo, você deseja que as teclas TAB e Enter sejam identificadas em uma caixa de texto.|Substitua <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Observação:**  Como alternativa, você pode manipular o <xref:System.Windows.Forms.Control.PreviewKeyDown> evento e o <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> conjunto de <xref:System.Windows.Forms.PreviewKeyDownEventArgs> para `true` para a chave ou as chaves desejadas.|  
|Execute tratamento de navegação ou entrada especial em um controle. Por exemplo, você deseja usar as teclas de seta no controle de lista para alterar o item selecionado.|Substituição<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Interceptar uma chave de navegação e <xref:System.Windows.Forms.Control.KeyPress> gerar um evento. Por exemplo, em um controle de caixa de rotação você deseja o pressionamento de várias teclas de seta para acelerar a progressão pelos itens.|Substitua <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Execute a manipulação especial de entrada ou navegação <xref:System.Windows.Forms.Control.KeyPress> durante um evento. Por exemplo, em uma controle de lista, manter pressionada a tecla "r" ignora os itens que começam com a letra r.|Substituição<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Execute o tratamento mnemônico personalizado. Por exemplo, você deseja manipular mnemônicos em botões desenhados pelo proprietário contidos em uma barra de ferramentas.|Substitua <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [Objeto My.Computer.Keyboard](../../visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [Acessando o Teclado](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [Usando eventos do teclado](using-keyboard-events.md)
