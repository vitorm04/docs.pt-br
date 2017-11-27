---
title: "Permissão negada (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5d7965ebd42cb3e56d66966d035be9ba3d3957c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="a492c-102">Permissão negada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a492c-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="a492c-103">Foi feita uma tentativa para gravar em um disco protegido contra gravação ou para acessar um arquivo bloqueado.</span><span class="sxs-lookup"><span data-stu-id="a492c-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a492c-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a492c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a492c-105">Para abrir um arquivo protegido contra gravação, altere o atributo de proteção contra gravação do arquivo.</span><span class="sxs-lookup"><span data-stu-id="a492c-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="a492c-106">Certifique-se de que o outro processo bloqueou o arquivo não e aguarde para abrir o arquivo até que outro processo solta.</span><span class="sxs-lookup"><span data-stu-id="a492c-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="a492c-107">Para acessar o registro, verifique suas permissões de usuário incluem esse tipo de acesso ao registro.</span><span class="sxs-lookup"><span data-stu-id="a492c-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a492c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a492c-108">See Also</span></span>  
 [<span data-ttu-id="a492c-109">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="a492c-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
