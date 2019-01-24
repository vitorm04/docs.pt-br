---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613812"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="5dff7-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5dff7-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="5dff7-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5dff7-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dff7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5dff7-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5dff7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5dff7-105">Methods</span></span>  
 <span data-ttu-id="5dff7-106">A classe MustUnderstandBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="5dff7-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5dff7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5dff7-107">Properties</span></span>  
 <span data-ttu-id="5dff7-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="5dff7-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="5dff7-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="5dff7-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="5dff7-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5dff7-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5dff7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5dff7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5dff7-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="5dff7-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dff7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5dff7-113">Requirements</span></span>  
  
|<span data-ttu-id="5dff7-114">MOF</span><span class="sxs-lookup"><span data-stu-id="5dff7-114">MOF</span></span>|<span data-ttu-id="5dff7-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5dff7-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5dff7-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="5dff7-116">Namespace</span></span>|<span data-ttu-id="5dff7-117">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5dff7-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dff7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dff7-118">See also</span></span>
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
