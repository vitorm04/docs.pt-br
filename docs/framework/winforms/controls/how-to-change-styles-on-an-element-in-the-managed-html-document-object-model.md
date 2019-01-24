---
title: 'Como: Alterar estilos em um elemento no modelo de objeto do documento HTML gerenciado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 0db67936e368c1cb6d942b348ebacd87b6127e19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579375"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Como: Alterar estilos em um elemento no modelo de objeto do documento HTML gerenciado
Você pode usar estilos em HTML para controlar a aparência de um documento e seus elementos. <xref:System.Windows.Forms.HtmlDocument> e <xref:System.Windows.Forms.HtmlElement> suporte <xref:System.Windows.Forms.HtmlElement.Style%2A> as propriedades que usam cadeias de caracteres de estilo no seguinte formato:  
  
 `name1:value1;...;nameN:valueN;`  
  
 Veja esse `DIV` com uma cadeia de caracteres de estilo que define a fonte como Arial e todo o texto como negrito:  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 O problema em manipular estilos usando o <xref:System.Windows.Forms.HtmlElement.Style%2A> é de propriedade que pode ser inconveniente para adicionar a e remover definições de estilo individuais da cadeia de caracteres. Por exemplo, seria um procedimento complexo renderizar o texto anterior em itálico sempre que o usuário posicionar o cursor sobre o `DIV` e remover o itálico quando o cursor deixar o `DIV`. O tempo poderia se tornar um problema se você precisasse manipular um grande número de estilos dessa maneira.  
  
 O procedimento a seguir contém o código que pode ser usado para manipular facilmente os estilos em documentos e elementos HTML. O procedimento exige que você saiba como executar tarefas básicas no Windows Forms, tal como criar um novo projeto e adicionar um controle a um formulário.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Processar as alterações de estilo em um Aplicativo do Windows Forms  
  
1.  Criar um novo projeto dos Windows Forms.  
  
2.  Crie um novo arquivo de classe terminando na extensão apropriada para sua linguagem de programação.  
  
3.  Copie o código de classe `StyleGenerator` na seção Exemplo deste tópico para o arquivo de classe e salve o código.  
  
4.  Salve o seguinte HTML em um arquivo chamado Test.htm.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Adicionar um <xref:System.Windows.Forms.WebBrowser> controle chamado `webBrowser1` ao formulário principal do seu projeto.  
  
6.  Adicione o seguinte código ao arquivo de código do seu projeto.  
  
    > [!IMPORTANT]
    >  Certifique-se de que o `webBrowser1_DocumentCompleted` manipulador de eventos é configurado como um ouvinte para o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> eventos. No Visual Studio, clique duas vezes no <xref:System.Windows.Forms.WebBrowser> controle; em um editor de texto, configure o ouvinte por meio de programação.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Execute o projeto. Passe o cursor pelo primeiro `DIV` para observar os efeitos do código.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra o código completo para a classe `StyleGenerator`, que analisa um valor de estilo existente, dá suporte à adição, alteração e remoção de estilos e retorna um novo valor de estilo com as alterações solicitadas.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.HtmlElement>
