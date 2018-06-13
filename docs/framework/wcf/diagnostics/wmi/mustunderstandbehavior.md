---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485551"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="a1366-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="a1366-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="a1366-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="a1366-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1366-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1366-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a1366-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a1366-105">Methods</span></span>  
 <span data-ttu-id="a1366-106">A classe MustUnderstandBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a1366-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1366-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a1366-107">Properties</span></span>  
 <span data-ttu-id="a1366-108">A classe MustUnderstandBehavior tem a seguinte propriedade:</span><span class="sxs-lookup"><span data-stu-id="a1366-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="a1366-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="a1366-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="a1366-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a1366-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1366-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a1366-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1366-112">Quando `true`, todos os cabeçalhos SOAP com o `MustUnderstand` atributo que não são manipuladas provocam esse comportamento lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="a1366-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1366-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1366-113">Requirements</span></span>  
  
|<span data-ttu-id="a1366-114">MOF</span><span class="sxs-lookup"><span data-stu-id="a1366-114">MOF</span></span>|<span data-ttu-id="a1366-115">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a1366-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1366-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="a1366-116">Namespace</span></span>|<span data-ttu-id="a1366-117">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a1366-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1366-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1366-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
