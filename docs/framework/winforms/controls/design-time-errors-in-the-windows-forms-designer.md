---
title: "Erros de tempo de design no Designer de Formulários do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62addf82929174d887160dadc4504cec19d9e3ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="68292-102">Erros de tempo de design no Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="68292-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="68292-103">Este tópico explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha.</span><span class="sxs-lookup"><span data-stu-id="68292-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="68292-104">Se essa lista de erros aparecer, não a interprete como um bug do designer, mas como um auxílio para a correção de erros no código.</span><span class="sxs-lookup"><span data-stu-id="68292-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="68292-105">Uma compreensão básica dessa lista de erros o ajudará a depurar aplicativos, fornecendo informações detalhadas sobre os erros e sugerindo possíveis soluções.</span><span class="sxs-lookup"><span data-stu-id="68292-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="68292-106">A Interface de Lista de Erros de Tempo de Design</span><span class="sxs-lookup"><span data-stu-id="68292-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="68292-107">Se o carregamento do Designer de Formulários do Windows falhar, uma lista de erros aparecerá no designer.</span><span class="sxs-lookup"><span data-stu-id="68292-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="68292-108">Os erros são agrupados em categorias.</span><span class="sxs-lookup"><span data-stu-id="68292-108">The errors are grouped into categories.</span></span> <span data-ttu-id="68292-109">Por exemplo, se houver quatro instâncias de variáveis não declaradas, eles serão agrupados na mesma categoria de erro.</span><span class="sxs-lookup"><span data-stu-id="68292-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="68292-110">Cada categoria de erro inclui uma breve descrição que resume o erro.</span><span class="sxs-lookup"><span data-stu-id="68292-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="68292-111">É possível expandir ou recolher uma categoria de erro clicando no título da categoria de erro ou clicando na divisa expandir/recolher.</span><span class="sxs-lookup"><span data-stu-id="68292-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="68292-112">Ao expandir uma categoria de erro, a ajuda adicional a seguir será exibida:</span><span class="sxs-lookup"><span data-stu-id="68292-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="68292-113">Instâncias desse erro.</span><span class="sxs-lookup"><span data-stu-id="68292-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="68292-114">Ajuda sobre esse erro.</span><span class="sxs-lookup"><span data-stu-id="68292-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="68292-115">Postagens do fórum sobre esse erro.</span><span class="sxs-lookup"><span data-stu-id="68292-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="68292-116">Instâncias Desse Erro</span><span class="sxs-lookup"><span data-stu-id="68292-116">Instances of This Error</span></span>  
 <span data-ttu-id="68292-117">A ajuda adicional lista todas as instâncias do erro no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="68292-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="68292-118">Muitos erros incluem um local exato no seguinte formato: *[Nome do Projeto]* *[Nome do Formulário]* Linha:*[Número de Linha]* Coluna:*[Número da Coluna]*.</span><span class="sxs-lookup"><span data-stu-id="68292-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="68292-119">O link **Ir para o Código** leva ao local do código em que o erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="68292-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="68292-120">Se uma pilha de chamadas estiver associada ao erro, será possível clicar no link **Mostrar Pilha de Chamadas**, que expande ainda mais o erro a fim de mostrar a pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="68292-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="68292-121">Examinar a pilha pode fornecer informações de depuração valiosas.</span><span class="sxs-lookup"><span data-stu-id="68292-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="68292-122">Por exemplo, é possível rastrear as funções chamadas antes da ocorrência do erro.</span><span class="sxs-lookup"><span data-stu-id="68292-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="68292-123">A pilha de chamadas é selecionável para que você possa copiá-la e salvá-la.</span><span class="sxs-lookup"><span data-stu-id="68292-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68292-124">No Visual Basic, a lista de erros de tempo de design não exibe mais de um erro, mas pode exibir várias instâncias do mesmo erro.</span><span class="sxs-lookup"><span data-stu-id="68292-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="68292-125">No Visual C++, os erros não links/links para número de linha para o código goto.</span><span class="sxs-lookup"><span data-stu-id="68292-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="68292-126">Ajuda com esse erro</span><span class="sxs-lookup"><span data-stu-id="68292-126">Help with This Error</span></span>  
 <span data-ttu-id="68292-127">Se o erro contiver um link para um tópico de ajuda associado do MSDN, a ajuda adicional incluirá um link para o tópico de ajuda.</span><span class="sxs-lookup"><span data-stu-id="68292-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="68292-128">Ao clicar no link, o tópico de ajuda associado aparecerá no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68292-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="68292-129">Postagens do fórum sobre este erro</span><span class="sxs-lookup"><span data-stu-id="68292-129">Forum posts about this error</span></span>  
 <span data-ttu-id="68292-130">A ajuda adicional incluirá um link para postagens no fórum do MSDN relacionadas ao erro.</span><span class="sxs-lookup"><span data-stu-id="68292-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="68292-131">Os fóruns são pesquisados com base na cadeia de caracteres da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="68292-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="68292-132">Também é possível tentar pesquisar os fóruns a seguir:</span><span class="sxs-lookup"><span data-stu-id="68292-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="68292-133">Fórum do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="68292-133">Windows Forms Designer Forum</span></span>](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="68292-134">Fóruns do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="68292-134">Windows Forms Forums</span></span>](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="68292-135">Ignorar e Continuar</span><span class="sxs-lookup"><span data-stu-id="68292-135">Ignore and Continue</span></span>  
 <span data-ttu-id="68292-136">É possível ignorar a condição de erro e continuar o carregamento do designer.</span><span class="sxs-lookup"><span data-stu-id="68292-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="68292-137">Escolher esta ação pode resultar em comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="68292-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="68292-138">Por exemplo, os controles podem não aparecer na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="68292-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68292-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68292-139">See Also</span></span>  
 [<span data-ttu-id="68292-140">Desenvolvimento de tempo de Design de solução de problemas</span><span class="sxs-lookup"><span data-stu-id="68292-140">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="68292-141">Solução de problemas de criação de controle e de componente</span><span class="sxs-lookup"><span data-stu-id="68292-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [<span data-ttu-id="68292-142">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="68292-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="68292-143">Mensagens de erro do Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="68292-143">Windows Forms Designer Error Messages</span></span>](http://msdn.microsoft.com/en-us/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
