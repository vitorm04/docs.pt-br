---
title: Unicode (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Unicode
dev_langs:
- VB
helpviewer_keywords:
- Unicode, external references
- Declare statement, marshaling strings
- Unicode keyword
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
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
ms.openlocfilehash: f75b5014d0bce247c484bd25a2c7ad00f2bbb66f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="unicode-visual-basic"></a><span data-ttu-id="aeb83-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aeb83-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="aeb83-103">Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode, independentemente do nome do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="aeb83-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="aeb83-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="aeb83-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="aeb83-105">Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa.</span><span class="sxs-lookup"><span data-stu-id="aeb83-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="aeb83-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="aeb83-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="aeb83-107">O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar strings durante uma chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="aeb83-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="aeb83-108">Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="aeb83-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="aeb83-109">O `Unicode` modificador Especifica que o Visual Basic deve empacotar todas as cadeias de caracteres para valores Unicode e deve consultar o procedimento sem modificar seu nome durante a pesquisa.</span><span class="sxs-lookup"><span data-stu-id="aeb83-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="aeb83-110">Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="aeb83-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aeb83-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="aeb83-111">Remarks</span></span>  
 <span data-ttu-id="aeb83-112">O `Unicode` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="aeb83-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="aeb83-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="aeb83-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="aeb83-114">Anotações de desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="aeb83-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="aeb83-115">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="aeb83-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb83-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aeb83-116">See Also</span></span>  
 <span data-ttu-id="aeb83-117">[ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) </span><span class="sxs-lookup"><span data-stu-id="aeb83-117">[Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) </span></span>  
<span data-ttu-id="aeb83-118"> [Automático](../../../visual-basic/language-reference/modifiers/auto.md) </span><span class="sxs-lookup"><span data-stu-id="aeb83-118"> [Auto](../../../visual-basic/language-reference/modifiers/auto.md) </span></span>  
<span data-ttu-id="aeb83-119"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="aeb83-119"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>
