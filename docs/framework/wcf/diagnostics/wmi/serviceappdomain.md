---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: aef0a0da9d107b92d9d3017968d5554205a6fd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485662"
---
# <a name="serviceappdomain"></a><span data-ttu-id="d948e-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="d948e-102">ServiceAppDomain</span></span>
<span data-ttu-id="d948e-103">Um serviço é mapeado para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d948e-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d948e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d948e-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d948e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d948e-105">Methods</span></span>  
 <span data-ttu-id="d948e-106">A classe ServiceAppDomain não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="d948e-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d948e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d948e-107">Properties</span></span>  
 <span data-ttu-id="d948e-108">A classe ServiceAppDomain tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d948e-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d948e-109">ref</span><span class="sxs-lookup"><span data-stu-id="d948e-109">ref</span></span>  
 <span data-ttu-id="d948e-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="d948e-110">Data type: Service</span></span>  
<span data-ttu-id="d948e-111">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="d948e-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="d948e-112">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d948e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d948e-113">O serviço desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d948e-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d948e-114">ref</span><span class="sxs-lookup"><span data-stu-id="d948e-114">ref</span></span>  
 <span data-ttu-id="d948e-115">Tipo de dados: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="d948e-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="d948e-116">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="d948e-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="d948e-117">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d948e-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d948e-118">Contém propriedades do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d948e-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d948e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d948e-119">Requirements</span></span>  
  
|<span data-ttu-id="d948e-120">MOF</span><span class="sxs-lookup"><span data-stu-id="d948e-120">MOF</span></span>|<span data-ttu-id="d948e-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d948e-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d948e-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="d948e-122">Namespace</span></span>|<span data-ttu-id="d948e-123">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d948e-123">Defined in root\ServiceModel</span></span>|
