---
title: "Sub ou função não definida (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
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
ms.openlocfilehash: 837beec039e1fb8f8a796b2781d93de6d4cfb33a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="747ab-102">Sub ou função não definida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="747ab-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="747ab-103">A `Sub` ou `Function` deve ser definido para ser chamado.</span><span class="sxs-lookup"><span data-stu-id="747ab-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="747ab-104">Possíveis causas do erro incluem:</span><span class="sxs-lookup"><span data-stu-id="747ab-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="747ab-105">Digitar incorretamente o nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="747ab-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="747ab-106">Tentar chamar um procedimento de outro projeto sem adicionar explicitamente uma referência a esse projeto no **referências** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="747ab-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="747ab-107">Especificar um procedimento que não é visível para o procedimento de chamada.</span><span class="sxs-lookup"><span data-stu-id="747ab-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="747ab-108">Declarar uma rotina de biblioteca de vínculo dinâmico (DLL) do Windows ou a rotina de recurso de código Macintosh que não está no recurso de biblioteca ou código especificado.</span><span class="sxs-lookup"><span data-stu-id="747ab-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="747ab-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="747ab-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="747ab-110">Certifique-se de que o nome do procedimento esteja escrito corretamente.</span><span class="sxs-lookup"><span data-stu-id="747ab-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="747ab-111">Localizar o nome do projeto que contém o procedimento que você deseja chamar o **referências** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="747ab-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="747ab-112">Se ele não aparecer, clique o **procurar** botão para procurá-lo.</span><span class="sxs-lookup"><span data-stu-id="747ab-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="747ab-113">Marque a caixa de seleção à esquerda do nome do projeto e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="747ab-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="747ab-114">Verifique o nome da rotina.</span><span class="sxs-lookup"><span data-stu-id="747ab-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="747ab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="747ab-115">See Also</span></span>  
 <span data-ttu-id="747ab-116">[Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="747ab-116">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="747ab-117"> [Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="747ab-117"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="747ab-118"> [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="747ab-118"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="747ab-119"> [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)</span><span class="sxs-lookup"><span data-stu-id="747ab-119"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)</span></span>
