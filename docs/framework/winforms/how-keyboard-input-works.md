---
title: Como a entrada do teclado funciona
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: a0b814a18f4a8b25fba9fa0b36da44954590f056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541340"
---
# <a name="how-keyboard-input-works"></a>Como a entrada do teclado funciona
O Windows Forms processa a entrada do teclado ao gerar eventos de teclado em resposta às mensagens do Windows. A maioria dos aplicativos Windows Forms processa a entrada do teclado exclusivamente ao manipular eventos de teclado. No entanto, você precisa entender como as mensagens do teclado funcionam para que você possa implementar cenários mais avançados de entrada do teclado, como interceptar teclas antes que elas atinjam um controle. Este tópico descreve os tipos de dados da chave que o Windows Forms reconhece e fornece uma visão geral de como as mensagens do teclado são roteadas. Para obter informações sobre eventos de teclado, consulte [Usando eventos do teclado](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Tipos de teclas  
 Windows Forms identifica a entrada do teclado como códigos de tecla virtuais que são representados por bit a bit <xref:System.Windows.Forms.Keys> enumeração. Com o <xref:System.Windows.Forms.Keys> enumeração, você pode combinar uma série de teclas pressionadas resultando em um único valor. Esses valores correspondem aos valores que acompanham as mensagens WM_KEYDOWN e WM_SYSKEYDOWN do Windows. Você pode detectar pressionamentos de teclas físicas mais manipulando o <xref:System.Windows.Forms.Control.KeyDown> ou <xref:System.Windows.Forms.Control.KeyUp> eventos. Teclas de caractere são um subconjunto do <xref:System.Windows.Forms.Keys> enumeração e correspondem aos valores que acompanham as mensagens do Windows WM_CHAR e WM_SYSCHAR. Se a combinação de teclas pressionadas resulta em um caractere, você pode detectar o caractere ao manipular o <xref:System.Windows.Forms.Control.KeyPress> evento. Como alternativa, você pode usar <xref:Microsoft.VisualBasic.Devices.Keyboard>, exposto pela interface de programação do Visual Basic, para descobrir quais teclas foram pressionadas e enviar teclas. Para obter mais informações, consulte [Acessando o teclado](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Ordem dos eventos do teclado  
 Conforme listado anteriormente, existem três eventos relacionados que podem ocorrer em um controle. A sequência a seguir mostra a ordem geral dos eventos:  
  
1.  O usuário pressiona a tecla "a", a chave é pré-processados distribuída e um <xref:System.Windows.Forms.Control.KeyDown> evento ocorre.  
  
2.  O usuário mantém a tecla "a", a chave é pré-processados distribuída e um <xref:System.Windows.Forms.Control.KeyPress> evento ocorre.  
  
     Esse evento ocorre várias vezes enquanto o usuário pressiona uma tecla.  
  
3.  O usuário solta a tecla "a", a chave é pré-processado, distribuída e um <xref:System.Windows.Forms.Control.KeyUp> evento ocorre.  
  
## <a name="preprocessing-keys"></a>Pré-processamento das teclas  
 Como outras mensagens, as mensagens do teclado são processadas no <xref:System.Windows.Forms.Control.WndProc%2A> método de um formulário ou controle. No entanto, antes de teclado as mensagens são processadas, o <xref:System.Windows.Forms.Control.PreProcessMessage%2A> um ou mais métodos que podem ser substituídos para manipular teclas de caracteres especiais e chaves físicas de chamadas de método. Você pode substituir esses métodos para detectar e filtrar certas teclas antes que as mensagens sejam processadas pelo controle. A tabela a seguir mostra a ação que está sendo executada e o método relacionado que ocorre, na ordem em que o método ocorre.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Pré-processamento de um evento KeyDown  
  
|Ação|Método relacionado|Observações|  
|------------|--------------------|-----------|  
|Verifique se há uma chave de comando como um acelerador ou um atalho de menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Este método processa uma chave de comando, que tem precedência sobre teclas regulares. Se esse método retornar `true`, a mensagem principal não será enviada e um evento de tecla não ocorrerá. Se ele retorna `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> é chamado`.`|  
|Verificar se há uma chave especial que requer pré-processamento ou uma tecla de caractere normal que deve gerar um <xref:System.Windows.Forms.Control.KeyDown> eventos e ser enviado para um controle.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Se o método retornar `true`, isso significa que o controle é um caractere normal e um <xref:System.Windows.Forms.Control.KeyDown> é gerado. Se `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> é chamado. **Observação:** para garantir que um controle receba uma chave ou uma combinação de teclas, você pode manipular o <xref:System.Windows.Forms.Control.PreviewKeyDown> evento e defina <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> do <xref:System.Windows.Forms.PreviewKeyDownEventArgs> para `true` para a chave ou teclas que você deseja.|  
|Verifique se há uma tecla de navegação (teclas ESC, TAB, Enter ou teclas de seta).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Este método processa uma tecla física que utiliza uma funcionalidade especial dentro do controle, como alternar o foco entre o controle e seu pai. Se o controle imediato não lidar com a chave, o <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> é chamado no controle pai e assim por diante, para o controle de nível superior na hierarquia. Se esse método retornar `true`, o pré-processamento estará completo e um evento de tecla não será gerado. Se ele retorna `false`, um <xref:System.Windows.Forms.Control.KeyDown> evento ocorre.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Pré-processamento de um evento KeyPress  
  
|Ação|Método relacionado|Observações|  
|------------|--------------------|-----------|  
|Verifique se a chave é um caractere normal que deve ser processado pelo controle|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Se o caractere é um caractere normal, este método retorna `true`, o <xref:System.Windows.Forms.Control.KeyPress> é gerado e não ocorrerá mais pré-processamento. Caso contrário, <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> será chamado.|  
|Verifique se o caractere é um mnemônico (como &OK em um botão)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Esse método, semelhante ao <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, será chamado até a hierarquia de controle. Se o controle for um controle de contêiner, ele procura mnemônicos chamando <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> em si mesmo e seus controles filhos. Se <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> retorna `true`, um <xref:System.Windows.Forms.Control.KeyPress> evento não ocorrerá.|  
  
## <a name="processing-keyboard-messages"></a>Processando mensagens do teclado  
 Depois que as mensagens do teclado alcance o <xref:System.Windows.Forms.Control.WndProc%2A> método de um controle ou formulário, eles são processados por um conjunto de métodos que podem ser substituídos. Cada um desses métodos retorna uma <xref:System.Boolean> valor que especifica se a mensagem teclado foi processada e consumida pelo controle. Se um dos métodos retornar `true`, então a mensagem será considerada tratada e ela não será passada para a base ou pai do controle para processamento adicional. Caso contrário, a mensagem permanecerá na fila e poderá ser processada em outro método da base ou pai do controle. A tabela a seguir apresenta os métodos que processam mensagens do teclado.  
  
|Método|Observações|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Este método processa todas as mensagens de teclado que são recebidas pelo <xref:System.Windows.Forms.Control.WndProc%2A> método do controle.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Esse método envia a mensagem do teclado para o pai do controle. Se <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> retorna `true`, nenhum evento-chave é gerado, caso contrário, <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> é chamado.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Este método gera o <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, e <xref:System.Windows.Forms.Control.KeyUp> eventos, conforme apropriado.|  
  
## <a name="overriding-keyboard-methods"></a>Substituindo métodos do teclado  
 Há vários métodos disponíveis para substituição quando uma mensagem do teclado é pré-processada e processada. No entanto, alguns métodos são opções muito melhores do que outros. A tabela a seguir mostra tarefas que você talvez queira realizar e a melhor maneira de substituir os métodos do teclado. Para obter mais informações sobre substituição de métodos, consulte [substituir propriedades e métodos em classes derivadas](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Tarefa|Método|  
|----------|------------|  
|Interceptar uma tecla de navegação e gerar um <xref:System.Windows.Forms.Control.KeyDown> eventos. Por exemplo, você deseja que as teclas TAB e Enter sejam identificadas em uma caixa de texto.|Substitua <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Observação:** como alternativa, você pode manipular o <xref:System.Windows.Forms.Control.PreviewKeyDown> evento e defina <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> do <xref:System.Windows.Forms.PreviewKeyDownEventArgs> para `true` para a chave ou teclas que você deseja.|  
|Execute tratamento de navegação ou entrada especial em um controle. Por exemplo, você deseja usar as teclas de seta no controle de lista para alterar o item selecionado.|Substituir <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Interceptar uma tecla de navegação e gerar um <xref:System.Windows.Forms.Control.KeyPress> eventos. Por exemplo, em um controle de caixa de rotação você deseja o pressionamento de várias teclas de seta para acelerar a progressão pelos itens.|Substitua <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Executar tratamento especial de entrada ou de navegação durante um <xref:System.Windows.Forms.Control.KeyPress> eventos. Por exemplo, em uma controle de lista, manter pressionada a tecla "r" ignora os itens que começam com a letra r.|Substituir <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Execute o tratamento mnemônico personalizado. Por exemplo, você deseja manipular mnemônicos em botões desenhados pelo proprietário contidos em uma barra de ferramentas.|Substitua <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [Objeto My.Computer.Keyboard](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [Acessando o Teclado](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [Usando eventos do teclado](../../../docs/framework/winforms/using-keyboard-events.md)
