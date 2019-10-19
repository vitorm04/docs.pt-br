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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583373"
---
# <a name="error-statement"></a><span data-ttu-id="28f6b-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="28f6b-102">Error Statement</span></span>
<span data-ttu-id="28f6b-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="28f6b-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28f6b-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="28f6b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="28f6b-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="28f6b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="28f6b-106">Required.</span></span> <span data-ttu-id="28f6b-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="28f6b-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28f6b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="28f6b-108">Remarks</span></span>  
 <span data-ttu-id="28f6b-109">A instrução `Error` tem suporte para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="28f6b-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="28f6b-110">No novo código, especialmente ao criar objetos, use o método `Raise` do objeto de `Err` para gerar erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="28f6b-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="28f6b-111">Se `errornumber` for definido, a instrução `Error` chamará o manipulador de erros depois que as propriedades do objeto `Err` forem atribuídas aos seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="28f6b-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="28f6b-112">propriedade</span><span class="sxs-lookup"><span data-stu-id="28f6b-112">Property</span></span>|<span data-ttu-id="28f6b-113">Valor</span><span class="sxs-lookup"><span data-stu-id="28f6b-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="28f6b-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="28f6b-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="28f6b-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="28f6b-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="28f6b-116">Nome do projeto de Visual Basic atual.</span><span class="sxs-lookup"><span data-stu-id="28f6b-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="28f6b-117">Expressão de cadeia de caracteres correspondente ao valor de retorno da função `Error` para o `Number` especificado, se essa cadeia de caracteres existir.</span><span class="sxs-lookup"><span data-stu-id="28f6b-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="28f6b-118">Se a cadeia de caracteres não existir, `Description` conterá uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="28f6b-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="28f6b-119">A unidade, o caminho e o nome de arquivo totalmente qualificados do arquivo de ajuda Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="28f6b-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="28f6b-120">A ID de contexto do arquivo de ajuda Visual Basic apropriada para o erro correspondente à propriedade `Number`.</span><span class="sxs-lookup"><span data-stu-id="28f6b-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="28f6b-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="28f6b-121">Zero.</span></span>|  
  
 <span data-ttu-id="28f6b-122">Se nenhum manipulador de erro existir, ou se nenhum estiver habilitado, uma mensagem de erro será criada e exibida a partir das propriedades do objeto de `Err`.</span><span class="sxs-lookup"><span data-stu-id="28f6b-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="28f6b-123">Alguns aplicativos host Visual Basic não podem criar objetos.</span><span class="sxs-lookup"><span data-stu-id="28f6b-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="28f6b-124">Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="28f6b-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f6b-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28f6b-125">Example</span></span>  
 <span data-ttu-id="28f6b-126">Este exemplo usa a instrução `Error` para gerar o erro número 11.</span><span class="sxs-lookup"><span data-stu-id="28f6b-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="28f6b-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28f6b-127">Requirements</span></span>  
 <span data-ttu-id="28f6b-128">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="28f6b-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="28f6b-129">**Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="28f6b-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28f6b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28f6b-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="28f6b-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="28f6b-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="28f6b-132">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="28f6b-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="28f6b-133">Mensagens de Erro</span><span class="sxs-lookup"><span data-stu-id="28f6b-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
