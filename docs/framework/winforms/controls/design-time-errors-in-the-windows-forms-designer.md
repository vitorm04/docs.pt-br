---
title: Erros de tempo de design no Designer de Formulários do Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015965"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="116e4-102">Erros de tempo de design no Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="116e4-102">Design-time errors in the Windows Forms Designer</span></span>

<span data-ttu-id="116e4-103">Este tópico explica o significado e o uso da lista de erros em tempo de design que aparece no Visual Studio quando o Designer de Formulários do Windows falha ao carregar.</span><span class="sxs-lookup"><span data-stu-id="116e4-103">This topic explains the meaning and use of the design-time error list that appears in Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="116e4-104">Se essa lista de erros aparecer, não a interprete como um bug do designer, mas como um auxílio para a correção de erros no código.</span><span class="sxs-lookup"><span data-stu-id="116e4-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>

<span data-ttu-id="116e4-105">Uma compreensão básica dessa lista de erros o ajudará a depurar aplicativos, fornecendo informações detalhadas sobre os erros e sugerindo possíveis soluções.</span><span class="sxs-lookup"><span data-stu-id="116e4-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>

## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="116e4-106">A interface da lista de erros em tempo de design</span><span class="sxs-lookup"><span data-stu-id="116e4-106">The design-time error list interface</span></span>

<span data-ttu-id="116e4-107">Se a Designer de Formulários do Windows falhar ao carregar, uma lista de erros aparecerá no designer.</span><span class="sxs-lookup"><span data-stu-id="116e4-107">If the Windows Forms Designer fails to load, an error list appears in the designer.</span></span> <span data-ttu-id="116e4-108">Os erros são agrupados em categorias.</span><span class="sxs-lookup"><span data-stu-id="116e4-108">The errors are grouped into categories.</span></span> <span data-ttu-id="116e4-109">Por exemplo, se houver quatro instâncias de variáveis não declaradas, eles serão agrupados na mesma categoria de erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="116e4-110">Cada categoria de erro inclui uma breve descrição que resume o erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-110">Each error category includes a brief description that summarizes the error.</span></span>

<span data-ttu-id="116e4-111">É possível expandir ou recolher uma categoria de erro clicando no título da categoria de erro ou clicando na divisa expandir/recolher.</span><span class="sxs-lookup"><span data-stu-id="116e4-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="116e4-112">Ao expandir uma categoria de erro, a ajuda adicional a seguir será exibida:</span><span class="sxs-lookup"><span data-stu-id="116e4-112">When you expand an error category, the following additional help is displayed:</span></span>

- <span data-ttu-id="116e4-113">Instâncias desse erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-113">Instances of this error.</span></span>

- <span data-ttu-id="116e4-114">Ajuda sobre esse erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-114">Help with this error.</span></span>

- <span data-ttu-id="116e4-115">Postagens do fórum sobre esse erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-115">Forum posts about this error.</span></span>

### <a name="instances-of-this-error"></a><span data-ttu-id="116e4-116">Instâncias desse erro</span><span class="sxs-lookup"><span data-stu-id="116e4-116">Instances of this error</span></span>

<span data-ttu-id="116e4-117">A ajuda adicional lista todas as instâncias do erro no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="116e4-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="116e4-118">Muitos erros incluem um local exato no seguinte formato: *[Nome do Projeto]* *[Nome do Formulário]* Linha: *[Número de Linha]* Coluna: *[Número da Coluna]* .</span><span class="sxs-lookup"><span data-stu-id="116e4-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="116e4-119">O link **Ir para o Código** leva ao local do código em que o erro ocorre.</span><span class="sxs-lookup"><span data-stu-id="116e4-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>

<span data-ttu-id="116e4-120">Se uma pilha de chamadas estiver associada ao erro, será possível clicar no link **Mostrar Pilha de Chamadas**, que expande ainda mais o erro a fim de mostrar a pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="116e4-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="116e4-121">Examinar a pilha pode fornecer informações de depuração valiosas.</span><span class="sxs-lookup"><span data-stu-id="116e4-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="116e4-122">Por exemplo, é possível rastrear as funções chamadas antes da ocorrência do erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="116e4-123">A pilha de chamadas é selecionável para que você possa copiá-la e salvá-la.</span><span class="sxs-lookup"><span data-stu-id="116e4-123">The call stack is selectable so that you can copy and save it.</span></span>

> [!NOTE]
> <span data-ttu-id="116e4-124">No Visual Basic, a lista de erros de tempo de design não exibe mais de um erro, mas pode exibir várias instâncias do mesmo erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="116e4-125">No Visual C++, os erros não links/links para número de linha para o código goto.</span><span class="sxs-lookup"><span data-stu-id="116e4-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>

### <a name="forum-posts-about-this-error"></a><span data-ttu-id="116e4-126">Postagens do fórum sobre este erro</span><span class="sxs-lookup"><span data-stu-id="116e4-126">Forum posts about this error</span></span>

<span data-ttu-id="116e4-127">A ajuda adicional inclui um link para postagens de fórum relacionadas ao erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-127">The additional help includes a link to forum posts related to the error.</span></span> <span data-ttu-id="116e4-128">Os fóruns são pesquisados com base na cadeia de caracteres da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="116e4-128">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="116e4-129">Você também pode tentar Pesquisar nos seguintes fóruns:</span><span class="sxs-lookup"><span data-stu-id="116e4-129">You can also try searching on the following forums:</span></span>

- [<span data-ttu-id="116e4-130">Fórum de Designer de Formulários do Windows</span><span class="sxs-lookup"><span data-stu-id="116e4-130">Windows Forms Designer forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [<span data-ttu-id="116e4-131">Fórum de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="116e4-131">Windows Forms forum</span></span>](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a><span data-ttu-id="116e4-132">Ignorar e continuar</span><span class="sxs-lookup"><span data-stu-id="116e4-132">Ignore and continue</span></span>

<span data-ttu-id="116e4-133">É possível ignorar a condição de erro e continuar o carregamento do designer.</span><span class="sxs-lookup"><span data-stu-id="116e4-133">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="116e4-134">Escolher esta ação pode resultar em comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="116e4-134">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="116e4-135">Por exemplo, os controles podem não aparecer na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="116e4-135">For example, controls may not appear on the design surface.</span></span>

## <a name="see-also"></a><span data-ttu-id="116e4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="116e4-136">See also</span></span>

- <span data-ttu-id="116e4-137">[Solução de problemas de desenvolvimento em tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="116e4-137">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
- [<span data-ttu-id="116e4-138">Solução de problemas de criação de controle e de componente</span><span class="sxs-lookup"><span data-stu-id="116e4-138">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)
- [<span data-ttu-id="116e4-139">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="116e4-139">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="116e4-140">[Mensagens de erro do Designer de Formulários do Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="116e4-140">[Windows Forms Designer Error Messages](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))</span></span>
