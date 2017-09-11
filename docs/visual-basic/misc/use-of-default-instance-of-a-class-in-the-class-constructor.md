---
title: "Uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e6ae82dd5186871f68b55ab21b9a57a5bca07d93
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="ba429-102">Uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita</span><span class="sxs-lookup"><span data-stu-id="ba429-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="ba429-103">Uma instância padrão de uma classe foi usada no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="ba429-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="ba429-104">Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="ba429-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ba429-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ba429-105">To correct this error</span></span>  
  
-   <span data-ttu-id="ba429-106">Remova a instância padrão do construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="ba429-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba429-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba429-107">See Also</span></span>  
 [<span data-ttu-id="ba429-108">NÃO está em compilação: Usando construtores e destruidores</span><span class="sxs-lookup"><span data-stu-id="ba429-108">NOT IN BUILD: Using Constructors and Destructors</span></span>](http://msdn.microsoft.com/en-us/548eebe1-86c4-4377-b2f5-447cb8be3d90)
