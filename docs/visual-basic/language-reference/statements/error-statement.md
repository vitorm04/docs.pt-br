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
ms.openlocfilehash: 8ac7cee2f9959bc75df165d00d3a0a67e1dd9af0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837527"
---
# <a name="error-statement"></a><span data-ttu-id="51cad-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="51cad-102">Error Statement</span></span>
<span data-ttu-id="51cad-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="51cad-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51cad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51cad-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="51cad-105">Partes</span><span class="sxs-lookup"><span data-stu-id="51cad-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="51cad-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="51cad-106">Required.</span></span> <span data-ttu-id="51cad-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="51cad-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51cad-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="51cad-108">Remarks</span></span>  
 <span data-ttu-id="51cad-109">O `Error` instrução é suportada para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="51cad-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="51cad-110">No novo código, especialmente ao criar objetos, use o `Err` do objeto `Raise` método para gerar erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="51cad-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="51cad-111">Se `errornumber` for definido, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="51cad-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="51cad-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="51cad-112">Property</span></span>|<span data-ttu-id="51cad-113">Valor</span><span class="sxs-lookup"><span data-stu-id="51cad-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="51cad-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="51cad-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="51cad-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="51cad-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="51cad-116">Nome do projeto atual do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="51cad-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="51cad-117">Expressão correspondente para o valor de retorno de cadeia de caracteres a `Error` função especificado `Number`, se essa cadeia de caracteres não existir.</span><span class="sxs-lookup"><span data-stu-id="51cad-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="51cad-118">Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="51cad-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="51cad-119">A unidade totalmente qualificada, o caminho e o nome do arquivo do arquivo de Ajuda do Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="51cad-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="51cad-120">ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic a `Number` propriedade.</span><span class="sxs-lookup"><span data-stu-id="51cad-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="51cad-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="51cad-121">Zero.</span></span>|  
  
 <span data-ttu-id="51cad-122">Se nenhum manipulador de erro existe, ou se nenhum estiver habilitado, uma mensagem de erro é criada e exibida do `Err` propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="51cad-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51cad-123">Alguns aplicativos de host do Visual Basic não é possível criar objetos.</span><span class="sxs-lookup"><span data-stu-id="51cad-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="51cad-124">Consulte a documentação do seu aplicativo de host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="51cad-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51cad-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="51cad-125">Example</span></span>  
 <span data-ttu-id="51cad-126">Este exemplo usa o `Error` instrução para gerar o erro número 11.</span><span class="sxs-lookup"><span data-stu-id="51cad-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="51cad-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51cad-127">Requirements</span></span>  
 <span data-ttu-id="51cad-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="51cad-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="51cad-129">**Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="51cad-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51cad-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51cad-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="51cad-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="51cad-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="51cad-132">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="51cad-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="51cad-133">Mensagens de Erro</span><span class="sxs-lookup"><span data-stu-id="51cad-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
