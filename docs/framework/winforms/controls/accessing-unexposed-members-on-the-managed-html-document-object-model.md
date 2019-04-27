---
title: Acessando membros não expostos no Document Object Model HTML gerenciado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011886"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="d9fd6-102">Acessando membros não expostos no Document Object Model HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="d9fd6-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="d9fd6-103">O gerenciado HTML documento Object Model (DOM) contém uma classe chamada <xref:System.Windows.Forms.HtmlElement> que expõe as propriedades, métodos e eventos que todos os elementos HTML têm em comum.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="d9fd6-104">Às vezes, no entanto, será necessário acessar membros que a interface gerenciada não expõe diretamente.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="d9fd6-105">Este tópico analisa duas maneiras de acessar membros não expostos, incluindo [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] e funções do VBScript definidas dentro de uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="d9fd6-106">Acessando Membros Não Expostos por meio de Interfaces Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="d9fd6-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="d9fd6-107"><xref:System.Windows.Forms.HtmlDocument> e <xref:System.Windows.Forms.HtmlElement> fornecem quatro métodos que permitem o acesso a membros não expostos.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="d9fd6-108">A tabela a seguir mostra os tipos e seus métodos correspondentes.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="d9fd6-109">Tipo do membro</span><span class="sxs-lookup"><span data-stu-id="d9fd6-109">Member Type</span></span>|<span data-ttu-id="d9fd6-110">Método(s)</span><span class="sxs-lookup"><span data-stu-id="d9fd6-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d9fd6-111">Propriedades (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="d9fd6-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="d9fd6-112">Métodos</span><span class="sxs-lookup"><span data-stu-id="d9fd6-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="d9fd6-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="d9fd6-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="d9fd6-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="d9fd6-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="d9fd6-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="d9fd6-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="d9fd6-116">Ao usar esses métodos, presume-se que se tem um elemento do tipo subjacente correto.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="d9fd6-117">Suponha que você queira escutar o evento `Submit` de um elemento `FORM` em uma página HTML, para que seja possível executar o pré-processamento nos valores de `FORM` antes de o usuário enviá-los para o servidor.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="d9fd6-118">Teoricamente, se tiver controle sobre a HTML, você definirá que o `FORM` terá um atributo `ID` único.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="d9fd6-119">Depois que você carregar esta página para o <xref:System.Windows.Forms.WebBrowser> controle, você pode usar o <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> método para recuperar o `FORM` em tempo de execução usando `form1` como o argumento.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="d9fd6-120">Acessando as Interfaces Não Gerenciadas</span><span class="sxs-lookup"><span data-stu-id="d9fd6-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="d9fd6-121">Também é possível acessar membros não expostos no HTML DOM gerenciado usando as interfaces Component Object Model (COM) não gerenciadas expostas por cada classe DOM.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="d9fd6-122">Isso será recomendado se for necessário fazer várias chamadas em membros não expostos ou se os membros não expostos retornarem outras interfaces não gerenciadas não encapsuladas pelo o HTML DOM gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="d9fd6-123">A tabela a seguir mostra todas as interfaces não gerenciadas expostas por meio do HTML DOM gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="d9fd6-124">Clique em cada link para obter uma explicação de seu uso e exemplos de código.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="d9fd6-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="d9fd6-125">Type</span></span>|<span data-ttu-id="d9fd6-126">Interface não gerenciada</span><span class="sxs-lookup"><span data-stu-id="d9fd6-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="d9fd6-127">A maneira mais fácil de usar as interfaces COM é adicionar uma referência à biblioteca de HTML DOM não gerenciada (MSHTML.dll) por meio do aplicativo, embora não haja suporte para isso.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="d9fd6-128">Para obter mais informações, consulte o [Artigo 934368 da base de dados de conhecimento](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="d9fd6-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="d9fd6-129">Acessando Funções de Script</span><span class="sxs-lookup"><span data-stu-id="d9fd6-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="d9fd6-130">Uma página HTML pode definir uma ou mais funções usando uma linguagem de script como [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ou VBScript.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="d9fd6-131">Essas funções são colocadas dentro de uma página `SCRIPT` na página e podem ser executadas sob demanda ou em resposta a um evento no DOM.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="d9fd6-132">Você pode chamar quaisquer funções de script que você define em uma página HTML usando o <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> método.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="d9fd6-133">Se o método de script retorna um elemento HTML, você pode usar uma conversão para converter o resultado retornado para um <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="d9fd6-134">Para obter detalhes e o código de exemplo, consulte <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="d9fd6-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9fd6-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9fd6-135">See also</span></span>

- [<span data-ttu-id="d9fd6-136">Usando o Modelo de Objeto do Documento HTML gerenciado</span><span class="sxs-lookup"><span data-stu-id="d9fd6-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
