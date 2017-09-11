---
title: ANSI (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
dev_langs:
- VB
helpviewer_keywords:
- Declare statement, marshaling strings
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1cc05b89de5aa9504769c294a04360f07ac81c7e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ansi-visual-basic"></a><span data-ttu-id="7b2fe-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b2fe-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="7b2fe-103">Especifica que o Visual Basic deve empacotar todas as strings para valores American National Standards Institute (ANSI) independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7b2fe-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="7b2fe-105">Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7b2fe-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7b2fe-107">O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="7b2fe-108">Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7b2fe-109">O `Ansi` modificador Especifica que o Visual Basic deve empacotar todas as strings para valores ANSI e deve consultar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="7b2fe-110">Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b2fe-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b2fe-111">Remarks</span></span>  
 <span data-ttu-id="7b2fe-112">O `Ansi` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="7b2fe-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7b2fe-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="7b2fe-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7b2fe-114">Anotações de desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="7b2fe-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7b2fe-115">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7b2fe-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2fe-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b2fe-116">See Also</span></span>  
 <span data-ttu-id="7b2fe-117">[Automático](../../../visual-basic/language-reference/modifiers/auto.md) </span><span class="sxs-lookup"><span data-stu-id="7b2fe-117">[Auto](../../../visual-basic/language-reference/modifiers/auto.md) </span></span>  
<span data-ttu-id="7b2fe-118"> [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) </span><span class="sxs-lookup"><span data-stu-id="7b2fe-118"> [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) </span></span>  
<span data-ttu-id="7b2fe-119"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="7b2fe-119"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>
