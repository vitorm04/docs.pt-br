---
title: A variável '<variablename>' é usada antes de receber um valor
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 46551a917aeb794c8d35985076b67a315386f628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819353"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="bdcdf-102">Variável '\<variablename >' é usada antes de receber um valor</span><span class="sxs-lookup"><span data-stu-id="bdcdf-102">Variable '\<variablename>' is used before it has been assigned a value</span></span>
<span data-ttu-id="bdcdf-103">Variável '\<variablename >' é usada antes de receber um valor.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="bdcdf-104">Uma exceção de referência nula poderia resultar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="bdcdf-105">Um aplicativo tem pelo menos um caminho possível pelo seu código que lê uma variável antes de qualquer valor é atribuído a ele.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="bdcdf-106">Se nunca tiver sido atribuída um valor uma variável, ele contém o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="bdcdf-107">Para um tipo de dados de referência, o valor padrão é [nada](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="bdcdf-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="bdcdf-108">Leitura de uma variável de referência que tem um valor de `Nothing` pode causar um <xref:System.NullReferenceException> em algumas circunstâncias.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="bdcdf-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-109">By default, this message is a warning.</span></span> <span data-ttu-id="bdcdf-110">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bdcdf-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bdcdf-111">**ID do erro:** BC42104</span><span class="sxs-lookup"><span data-stu-id="bdcdf-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bdcdf-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="bdcdf-112">To correct this error</span></span>  
  
-   <span data-ttu-id="bdcdf-113">Verifique sua lógica de fluxo de controle e verifique se que a variável tem um valor válido antes do controle passa para qualquer instrução que lê-lo.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="bdcdf-114">É uma maneira de garantir que a variável sempre tem um valor válido para inicializá-lo como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="bdcdf-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="bdcdf-115">Consulte "Inicialização" no [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bdcdf-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdcdf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdcdf-116">See also</span></span>

- [<span data-ttu-id="bdcdf-117">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="bdcdf-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="bdcdf-118">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="bdcdf-118">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="bdcdf-119">Solução de problemas de Variáveis</span><span class="sxs-lookup"><span data-stu-id="bdcdf-119">Troubleshooting Variables</span></span>](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
