---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6838c6ce98e0d373a45c136b12bdedbd8c9eb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="56e41-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="56e41-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="56e41-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="56e41-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e41-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56e41-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="56e41-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="56e41-105">Methods</span></span>  
 <span data-ttu-id="56e41-106">A classe MustUnderstandBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="56e41-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="56e41-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="56e41-107">Properties</span></span>  
 <span data-ttu-id="56e41-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="56e41-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="56e41-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="56e41-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="56e41-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="56e41-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="56e41-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="56e41-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56e41-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="56e41-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56e41-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56e41-113">Requirements</span></span>  
  
|<span data-ttu-id="56e41-114">MOF</span><span class="sxs-lookup"><span data-stu-id="56e41-114">MOF</span></span>|<span data-ttu-id="56e41-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="56e41-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="56e41-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="56e41-116">Namespace</span></span>|<span data-ttu-id="56e41-117">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="56e41-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56e41-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56e41-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
