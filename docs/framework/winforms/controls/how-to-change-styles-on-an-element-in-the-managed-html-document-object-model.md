---
title: Como alterar estilos em um elemento no Document Object Model HTML gerenciado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3726ccdebf310d831fb0d7ea21fab011293f6d99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="d0ec1-102">Como alterar estilos em um elemento no Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="d0ec1-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="d0ec1-103">Você pode usar estilos em HTML para controlar a aparência de um documento e seus elementos.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="d0ec1-104"><xref:System.Windows.Forms.HtmlDocument>e <xref:System.Windows.Forms.HtmlElement> suporte <xref:System.Windows.Forms.HtmlElement.Style%2A> propriedades que usam cadeias de caracteres de estilo do seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="d0ec1-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>  
  
 `name1:value1;...;nameN:valueN;`  
  
 <span data-ttu-id="d0ec1-105">Veja esse `DIV` com uma cadeia de caracteres de estilo que define a fonte como Arial e todo o texto como negrito:</span><span class="sxs-lookup"><span data-stu-id="d0ec1-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 <span data-ttu-id="d0ec1-106">O problema com a manipulação de estilos usando o <xref:System.Windows.Forms.HtmlElement.Style%2A> é de propriedade que pode ser inconveniente para adicionar a e remover definições de estilo individuais da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="d0ec1-107">Por exemplo, seria um procedimento complexo renderizar o texto anterior em itálico sempre que o usuário posicionar o cursor sobre o `DIV` e remover o itálico quando o cursor deixar o `DIV`.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="d0ec1-108">O tempo poderia se tornar um problema se você precisasse manipular um grande número de estilos dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>  
  
 <span data-ttu-id="d0ec1-109">O procedimento a seguir contém o código que pode ser usado para manipular facilmente os estilos em documentos e elementos HTML.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="d0ec1-110">O procedimento exige que você saiba como executar tarefas básicas no Windows Forms, tal como criar um novo projeto e adicionar um controle a um formulário.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="d0ec1-111">Processar as alterações de estilo em um Aplicativo do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0ec1-111">To process style changes in a Windows Forms application</span></span>  
  
1.  <span data-ttu-id="d0ec1-112">Criar um novo projeto dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-112">Create a new Windows Forms project.</span></span>  
  
2.  <span data-ttu-id="d0ec1-113">Crie um novo arquivo de classe terminando na extensão apropriada para sua linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>  
  
3.  <span data-ttu-id="d0ec1-114">Copie o código de classe `StyleGenerator` na seção Exemplo deste tópico para o arquivo de classe e salve o código.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>  
  
4.  <span data-ttu-id="d0ec1-115">Salve o seguinte HTML em um arquivo chamado Test.htm.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-115">Save the following HTML to a file named Test.htm.</span></span>  
  
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
  
5.  <span data-ttu-id="d0ec1-116">Adicionar um <xref:System.Windows.Forms.WebBrowser> controle chamado `webBrowser1` ao formulário principal de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>  
  
6.  <span data-ttu-id="d0ec1-117">Adicione o seguinte código ao arquivo de código do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-117">Add the following code to your project's code file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d0ec1-118">Certifique-se de que o `webBrowser1_DocumentCompleted` manipulador de eventos é configurado como um ouvinte para o <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> evento.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-118">Ensure that the `webBrowser1_DocumentCompleted` event hander is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="d0ec1-119">Em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], clique duas vezes no <xref:System.Windows.Forms.WebBrowser> controlar; em um editor de texto, configurar o ouvinte de forma programática.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-119">In [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  <span data-ttu-id="d0ec1-120">Execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-120">Run the project.</span></span> <span data-ttu-id="d0ec1-121">Passe o cursor pelo primeiro `DIV` para observar os efeitos do código.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ec1-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0ec1-122">Example</span></span>  
 <span data-ttu-id="d0ec1-123">O exemplo de código a seguir mostra o código completo para a classe `StyleGenerator`, que analisa um valor de estilo existente, dá suporte à adição, alteração e remoção de estilos e retorna um novo valor de estilo com as alterações solicitadas.</span><span class="sxs-lookup"><span data-stu-id="d0ec1-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d0ec1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0ec1-124">See Also</span></span>  
 <xref:System.Windows.Forms.HtmlElement>
