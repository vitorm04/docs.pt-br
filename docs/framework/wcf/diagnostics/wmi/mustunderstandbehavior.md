---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165446"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="b447b-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b447b-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="b447b-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b447b-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b447b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b447b-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b447b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b447b-105">Methods</span></span>  
 <span data-ttu-id="b447b-106">A classe MustUnderstandBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="b447b-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b447b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b447b-107">Properties</span></span>  
 <span data-ttu-id="b447b-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="b447b-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="b447b-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="b447b-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="b447b-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b447b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b447b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="b447b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b447b-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b447b-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b447b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b447b-113">Requirements</span></span>  
  
|<span data-ttu-id="b447b-114">MOF</span><span class="sxs-lookup"><span data-stu-id="b447b-114">MOF</span></span>|<span data-ttu-id="b447b-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b447b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b447b-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="b447b-116">Namespace</span></span>|<span data-ttu-id="b447b-117">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b447b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b447b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b447b-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
