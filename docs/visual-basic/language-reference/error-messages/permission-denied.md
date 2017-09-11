---
title: "Permissão negada (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID70
dev_langs:
- VB
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 8
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
ms.openlocfilehash: 25ac8a2262c403b529a23b36667eaf23eda55af6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="d1024-102">Permissão negada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1024-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="d1024-103">Foi feita uma tentativa para gravar em um disco protegido contra gravação ou para acessar um arquivo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="d1024-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1024-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d1024-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="d1024-105">Para abrir um arquivo protegido contra gravação, altere o atributo proteção contra gravação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d1024-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="d1024-106">Certifique-se de que outro processo não bloqueou o arquivo e esperar para abri-lo até que o outro processo o libere.</span><span class="sxs-lookup"><span data-stu-id="d1024-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="d1024-107">Para acessar o registro, verifique se as permissões do usuário incluem esse tipo de acesso ao registro.</span><span class="sxs-lookup"><span data-stu-id="d1024-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1024-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1024-108">See Also</span></span>  
 [<span data-ttu-id="d1024-109">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="d1024-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
