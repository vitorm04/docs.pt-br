---
title: Erro no carregamento da DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 5a26443a49b0b853f2f2188fb58d7ed907d671b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659609"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="be1ce-102">Erro no carregamento da DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be1ce-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="be1ce-103">Uma biblioteca de vínculo dinâmico (DLL) é uma biblioteca especificada na `Lib` cláusula de um `Declare` instrução.</span><span class="sxs-lookup"><span data-stu-id="be1ce-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="be1ce-104">Possíveis causas para esse erro incluem:</span><span class="sxs-lookup"><span data-stu-id="be1ce-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="be1ce-105">O arquivo não é executável da DLL.</span><span class="sxs-lookup"><span data-stu-id="be1ce-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="be1ce-106">O arquivo não é uma DLL do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="be1ce-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="be1ce-107">A DLL faz referência a outro DLL que não está presente.</span><span class="sxs-lookup"><span data-stu-id="be1ce-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="be1ce-108">A DLL ou DLL referenciada não está em um diretório especificado no caminho.</span><span class="sxs-lookup"><span data-stu-id="be1ce-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be1ce-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be1ce-109">To correct this error</span></span>  
  
- <span data-ttu-id="be1ce-110">Se o arquivo for um arquivo de texto de origem e, portanto, não DLL executável, ele deve ser compilado e vinculado a um formulário de DLL executável.</span><span class="sxs-lookup"><span data-stu-id="be1ce-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="be1ce-111">Se o arquivo não é uma DLL do Microsoft Windows, obtenha o Windows Microsoft equivalente.</span><span class="sxs-lookup"><span data-stu-id="be1ce-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="be1ce-112">Se a DLL referências outro DLL que não está presente, obtenha a DLL de referência e disponibilizá-lo.</span><span class="sxs-lookup"><span data-stu-id="be1ce-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="be1ce-113">Se a DLL ou DLL referenciada não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.</span><span class="sxs-lookup"><span data-stu-id="be1ce-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1ce-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be1ce-114">See also</span></span>

- [<span data-ttu-id="be1ce-115">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="be1ce-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
