---
title: Instrução Error
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
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351243"
---
# <a name="error-statement"></a><span data-ttu-id="57aa1-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="57aa1-102">Error Statement</span></span>
<span data-ttu-id="57aa1-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="57aa1-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57aa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57aa1-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="57aa1-105">Partes</span><span class="sxs-lookup"><span data-stu-id="57aa1-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="57aa1-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="57aa1-106">Required.</span></span> <span data-ttu-id="57aa1-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="57aa1-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57aa1-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="57aa1-108">Remarks</span></span>  
 <span data-ttu-id="57aa1-109">A instrução `Error` tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="57aa1-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="57aa1-110">No novo código, especialmente ao criar objetos, use o método `Raise` do objeto de `Err` para gerar erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="57aa1-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="57aa1-111">Se `errornumber` for definido, a instrução `Error` chamará o manipulador de erros depois que as propriedades do objeto `Err` forem atribuídas aos seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="57aa1-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="57aa1-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="57aa1-112">Property</span></span>|<span data-ttu-id="57aa1-113">Valor</span><span class="sxs-lookup"><span data-stu-id="57aa1-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="57aa1-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="57aa1-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="57aa1-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="57aa1-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="57aa1-116">Nome do projeto de Visual Basic atual.</span><span class="sxs-lookup"><span data-stu-id="57aa1-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="57aa1-117">Expressão de cadeia de caracteres correspondente ao valor de retorno da função `Error` para o `Number`especificado, se essa cadeia de caracteres existir.</span><span class="sxs-lookup"><span data-stu-id="57aa1-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="57aa1-118">Se a cadeia de caracteres não existir, `Description` conterá uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="57aa1-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="57aa1-119">A unidade, o caminho e o nome de arquivo totalmente qualificados do arquivo de ajuda Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="57aa1-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="57aa1-120">A ID de contexto do arquivo de ajuda Visual Basic apropriada para o erro correspondente à propriedade `Number`.</span><span class="sxs-lookup"><span data-stu-id="57aa1-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="57aa1-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="57aa1-121">Zero.</span></span>|  
  
 <span data-ttu-id="57aa1-122">Se nenhum manipulador de erro existir, ou se nenhum estiver habilitado, uma mensagem de erro será criada e exibida a partir das propriedades do objeto de `Err`.</span><span class="sxs-lookup"><span data-stu-id="57aa1-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57aa1-123">Alguns aplicativos host Visual Basic não podem criar objetos.</span><span class="sxs-lookup"><span data-stu-id="57aa1-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="57aa1-124">Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="57aa1-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57aa1-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="57aa1-125">Example</span></span>  
 <span data-ttu-id="57aa1-126">Este exemplo usa a instrução `Error` para gerar o erro número 11.</span><span class="sxs-lookup"><span data-stu-id="57aa1-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="57aa1-127">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="57aa1-127">Requirements</span></span>  
 <span data-ttu-id="57aa1-128">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="57aa1-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="57aa1-129">**Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="57aa1-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57aa1-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57aa1-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="57aa1-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="57aa1-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="57aa1-132">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="57aa1-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="57aa1-133">Mensagens de Erro</span><span class="sxs-lookup"><span data-stu-id="57aa1-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
