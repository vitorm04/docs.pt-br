---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975333"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="51476-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="51476-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="51476-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="51476-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51476-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51476-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51476-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="51476-105">Methods</span></span>  
 <span data-ttu-id="51476-106">A classe MustUnderstandBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="51476-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51476-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="51476-107">Properties</span></span>  
 <span data-ttu-id="51476-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="51476-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="51476-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="51476-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="51476-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="51476-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="51476-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="51476-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51476-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="51476-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51476-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51476-113">Requirements</span></span>  
  
|<span data-ttu-id="51476-114">MOF</span><span class="sxs-lookup"><span data-stu-id="51476-114">MOF</span></span>|<span data-ttu-id="51476-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="51476-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51476-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="51476-116">Namespace</span></span>|<span data-ttu-id="51476-117">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="51476-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51476-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51476-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
