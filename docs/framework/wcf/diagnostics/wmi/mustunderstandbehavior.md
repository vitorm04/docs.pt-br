---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49371790"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="5c030-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5c030-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="5c030-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5c030-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c030-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5c030-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5c030-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5c030-105">Methods</span></span>  
 <span data-ttu-id="5c030-106">A classe MustUnderstandBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="5c030-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5c030-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5c030-107">Properties</span></span>  
 <span data-ttu-id="5c030-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="5c030-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="5c030-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="5c030-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="5c030-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5c030-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5c030-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="5c030-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5c030-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5c030-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c030-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5c030-113">Requirements</span></span>  
  
|<span data-ttu-id="5c030-114">MOF</span><span class="sxs-lookup"><span data-stu-id="5c030-114">MOF</span></span>|<span data-ttu-id="5c030-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5c030-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5c030-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="5c030-116">Namespace</span></span>|<span data-ttu-id="5c030-117">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5c030-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c030-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c030-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
