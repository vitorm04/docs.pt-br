---
title: "Automático (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Auto
dev_langs:
- VB
helpviewer_keywords:
- Auto keyword, external references
- Declare statement, marshaling strings
- Auto keyword
- Auto keyword, marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
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
ms.openlocfilehash: c315eb9f12e2d10b2f39f6546111ad56b50e5b23
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="auto-visual-basic"></a><span data-ttu-id="92b12-102">Auto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b12-102">Auto (Visual Basic)</span></span>
<span data-ttu-id="92b12-103">Especifica que o Visual Basic deve empacotar cadeias de caracteres de acordo com as regras do .NET Framework com base no nome externo do procedimento externo que está sendo declarado.</span><span class="sxs-lookup"><span data-stu-id="92b12-103">Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="92b12-104">Quando você chama um procedimento definido fora do seu projeto, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente.</span><span class="sxs-lookup"><span data-stu-id="92b12-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly.</span></span> <span data-ttu-id="92b12-105">Esta informação inclui onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o caractere da cadeia de caracteres conjunto que ele usa.</span><span class="sxs-lookup"><span data-stu-id="92b12-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="92b12-106">O [instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md) cria uma referência a um procedimento externo e fornece esta informação necessária.</span><span class="sxs-lookup"><span data-stu-id="92b12-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="92b12-107">O `charsetmodifier` parte o `Declare` instrução fornece a informação do conjunto de caracteres para empacotar cadeias de caracteres durante a chamada ao procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="92b12-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="92b12-108">Ele também afeta como o Visual Basic procura o arquivo externo para o nome do procedimento externo.</span><span class="sxs-lookup"><span data-stu-id="92b12-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="92b12-109">O `Auto` modificador Especifica Visual Basic deve realizar marshaling de cadeias de caracteres de acordo com as regras do .NET Framework e que ele deve determinar o caractere base definido da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo se a pesquisa inicial falhar.</span><span class="sxs-lookup"><span data-stu-id="92b12-109">The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails.</span></span> <span data-ttu-id="92b12-110">Para obter mais informações, consulte "Conjuntos de caracteres" [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92b12-110">For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).</span></span>  
  
 <span data-ttu-id="92b12-111">Se nenhum modificador de conjunto de caracteres é especificado, `Ansi` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="92b12-111">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b12-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="92b12-112">Remarks</span></span>  
 <span data-ttu-id="92b12-113">O `Auto` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="92b12-113">The `Auto` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="92b12-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="92b12-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="92b12-115">Anotações de desenvolvedor de dispositivo inteligente</span><span class="sxs-lookup"><span data-stu-id="92b12-115">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="92b12-116">Não há suporte para essa palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="92b12-116">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b12-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92b12-117">See Also</span></span>  
 <span data-ttu-id="92b12-118">[ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) </span><span class="sxs-lookup"><span data-stu-id="92b12-118">[Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) </span></span>  
<span data-ttu-id="92b12-119"> [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) </span><span class="sxs-lookup"><span data-stu-id="92b12-119"> [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) </span></span>  
<span data-ttu-id="92b12-120"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)</span><span class="sxs-lookup"><span data-stu-id="92b12-120"> [Keywords](../../../visual-basic/language-reference/keywords/index.md)</span></span>
