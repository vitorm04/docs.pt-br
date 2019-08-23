---
title: Instrução Error (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944450"
---
# <a name="error-statement"></a><span data-ttu-id="84fc7-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="84fc7-102">Error Statement</span></span>
<span data-ttu-id="84fc7-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="84fc7-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fc7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84fc7-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="84fc7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="84fc7-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="84fc7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="84fc7-106">Required.</span></span> <span data-ttu-id="84fc7-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="84fc7-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84fc7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="84fc7-108">Remarks</span></span>  
 <span data-ttu-id="84fc7-109">A `Error` instrução tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="84fc7-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="84fc7-110">No novo código, especialmente ao criar objetos, use o `Err` método do `Raise` objeto para gerar erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="84fc7-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="84fc7-111">Se `errornumber` for definido, a `Error` instrução chamará o manipulador de erro `Err` depois que as propriedades do objeto forem atribuídas aos seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="84fc7-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="84fc7-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="84fc7-112">Property</span></span>|<span data-ttu-id="84fc7-113">Valor</span><span class="sxs-lookup"><span data-stu-id="84fc7-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="84fc7-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="84fc7-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="84fc7-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="84fc7-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="84fc7-116">Nome do projeto de Visual Basic atual.</span><span class="sxs-lookup"><span data-stu-id="84fc7-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="84fc7-117">Expressão de cadeia de caracteres correspondente ao valor de `Error` retorno da função para `Number`o especificado, se essa cadeia de caracteres existir.</span><span class="sxs-lookup"><span data-stu-id="84fc7-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="84fc7-118">Se a cadeia de caracteres não existir `Description` , conterá uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="84fc7-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="84fc7-119">A unidade, o caminho e o nome de arquivo totalmente qualificados do arquivo de ajuda Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="84fc7-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="84fc7-120">A ID de contexto do arquivo de ajuda Visual Basic apropriada para o erro `Number` correspondente à propriedade.</span><span class="sxs-lookup"><span data-stu-id="84fc7-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="84fc7-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="84fc7-121">Zero.</span></span>|  
  
 <span data-ttu-id="84fc7-122">Se nenhum manipulador de erro existir, ou se nenhum estiver habilitado, uma mensagem de erro será criada e exibida `Err` nas propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="84fc7-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84fc7-123">Alguns aplicativos host Visual Basic não podem criar objetos.</span><span class="sxs-lookup"><span data-stu-id="84fc7-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="84fc7-124">Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="84fc7-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84fc7-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="84fc7-125">Example</span></span>  
 <span data-ttu-id="84fc7-126">Este exemplo usa a `Error` instrução para gerar o número de erro 11.</span><span class="sxs-lookup"><span data-stu-id="84fc7-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="84fc7-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84fc7-127">Requirements</span></span>  
 <span data-ttu-id="84fc7-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="84fc7-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="84fc7-129">**)** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="84fc7-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fc7-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84fc7-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="84fc7-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="84fc7-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="84fc7-132">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="84fc7-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="84fc7-133">Mensagens de Erro</span><span class="sxs-lookup"><span data-stu-id="84fc7-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
