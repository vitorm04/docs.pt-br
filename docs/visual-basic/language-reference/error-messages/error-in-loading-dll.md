---
title: Erro ao carregar DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409615"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="06f3e-102">Erro no carregamento da DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06f3e-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="06f3e-103">Uma DLL (biblioteca de vínculo dinâmico) é uma biblioteca especificada na `Lib` cláusula de uma `Declare` instrução.</span><span class="sxs-lookup"><span data-stu-id="06f3e-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="06f3e-104">Possíveis causas desse erro incluem:</span><span class="sxs-lookup"><span data-stu-id="06f3e-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="06f3e-105">O arquivo não é executável de DLL.</span><span class="sxs-lookup"><span data-stu-id="06f3e-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="06f3e-106">O arquivo não é uma DLL do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="06f3e-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="06f3e-107">A DLL faz referência a outra DLL que não está presente.</span><span class="sxs-lookup"><span data-stu-id="06f3e-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="06f3e-108">A DLL ou a DLL referenciada não está em um diretório especificado no caminho.</span><span class="sxs-lookup"><span data-stu-id="06f3e-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="06f3e-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="06f3e-109">To correct this error</span></span>  
  
- <span data-ttu-id="06f3e-110">Se o arquivo for um arquivo de texto de origem e, portanto, não executável de DLL, ele deverá ser compilado e vinculado a um formulário executável DLL.</span><span class="sxs-lookup"><span data-stu-id="06f3e-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="06f3e-111">Se o arquivo não for uma DLL do Microsoft Windows, obtenha o equivalente do Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="06f3e-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="06f3e-112">Se a DLL fizer referência a outra DLL que não está presente, obtenha a DLL referenciada e torne-a disponível.</span><span class="sxs-lookup"><span data-stu-id="06f3e-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="06f3e-113">Se a dll ou a DLL referenciada não estiver em um diretório especificado pelo caminho, mova a DLL para um diretório referenciado.</span><span class="sxs-lookup"><span data-stu-id="06f3e-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f3e-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="06f3e-114">See also</span></span>

- [<span data-ttu-id="06f3e-115">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="06f3e-115">Declare Statement</span></span>](../statements/declare-statement.md)
