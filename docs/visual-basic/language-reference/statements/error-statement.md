---
title: Instrução Error
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a><span data-ttu-id="ed63b-102">Instrução Error</span><span class="sxs-lookup"><span data-stu-id="ed63b-102">Error Statement</span></span>
<span data-ttu-id="ed63b-103">Simula a ocorrência de um erro.</span><span class="sxs-lookup"><span data-stu-id="ed63b-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed63b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed63b-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="ed63b-105">Partes</span><span class="sxs-lookup"><span data-stu-id="ed63b-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="ed63b-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="ed63b-106">Required.</span></span> <span data-ttu-id="ed63b-107">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="ed63b-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed63b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed63b-108">Remarks</span></span>  
 <span data-ttu-id="ed63b-109">O `Error` instrução é suportada para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ed63b-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="ed63b-110">No novo código, especialmente ao criar objetos, use o `Err` do objeto `Raise` método para gerar erros de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ed63b-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="ed63b-111">Se `errornumber` for definida, o `Error` instrução chama o manipulador de erro após as propriedades do `Err` objeto são atribuídos os seguintes valores padrão:</span><span class="sxs-lookup"><span data-stu-id="ed63b-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="ed63b-112">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ed63b-112">Property</span></span>|<span data-ttu-id="ed63b-113">Valor</span><span class="sxs-lookup"><span data-stu-id="ed63b-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="ed63b-114">Valor especificado como argumento para `Error` instrução.</span><span class="sxs-lookup"><span data-stu-id="ed63b-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="ed63b-115">Pode ser qualquer número de erro válido.</span><span class="sxs-lookup"><span data-stu-id="ed63b-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="ed63b-116">Nome do projeto do Visual Basic atual.</span><span class="sxs-lookup"><span data-stu-id="ed63b-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="ed63b-117">Expressão correspondente para o valor de retorno de cadeia de caracteres de `Error` função especificado `Number`, se existir essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ed63b-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="ed63b-118">Se a cadeia de caracteres não existir, `Description` contém uma cadeia de caracteres de comprimento zero ("").</span><span class="sxs-lookup"><span data-stu-id="ed63b-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="ed63b-119">A unidade totalmente qualificada, o caminho e o nome do arquivo de Ajuda do Visual Basic apropriado.</span><span class="sxs-lookup"><span data-stu-id="ed63b-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="ed63b-120">ID de contexto para o erro correspondente de arquivos de ajuda Visual Basic o `Number` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ed63b-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="ed63b-121">Zero.</span><span class="sxs-lookup"><span data-stu-id="ed63b-121">Zero.</span></span>|  
  
 <span data-ttu-id="ed63b-122">Se nenhum manipulador de erro existe, ou se nenhum estiver habilitado, uma mensagem de erro é criada e exibida a partir de `Err` propriedades do objeto.</span><span class="sxs-lookup"><span data-stu-id="ed63b-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed63b-123">Alguns aplicativos de host do Visual Basic não podem criar objetos.</span><span class="sxs-lookup"><span data-stu-id="ed63b-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="ed63b-124">Consulte a documentação do aplicativo host para determinar se ele pode criar classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="ed63b-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed63b-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ed63b-125">Example</span></span>  
 <span data-ttu-id="ed63b-126">Este exemplo usa o `Error` instrução para gerar o erro número 11.</span><span class="sxs-lookup"><span data-stu-id="ed63b-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="ed63b-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed63b-127">Requirements</span></span>  
 <span data-ttu-id="ed63b-128">**Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ed63b-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ed63b-129">**Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ed63b-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed63b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed63b-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="ed63b-131">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="ed63b-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="ed63b-132">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="ed63b-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="ed63b-133">Mensagens de Erro</span><span class="sxs-lookup"><span data-stu-id="ed63b-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
