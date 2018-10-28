---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192233"
---
# <a name="serviceappdomain"></a><span data-ttu-id="f3ed1-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="f3ed1-102">ServiceAppDomain</span></span>
<span data-ttu-id="f3ed1-103">Mapeia um serviço para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3ed1-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ed1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3ed1-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3ed1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f3ed1-105">Methods</span></span>  
 <span data-ttu-id="f3ed1-106">A classe ServiceAppDomain não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="f3ed1-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3ed1-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f3ed1-107">Properties</span></span>  
 <span data-ttu-id="f3ed1-108">A classe ServiceAppDomain tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f3ed1-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f3ed1-109">ref</span><span class="sxs-lookup"><span data-stu-id="f3ed1-109">ref</span></span>  
 <span data-ttu-id="f3ed1-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="f3ed1-110">Data type: Service</span></span>  
<span data-ttu-id="f3ed1-111">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="f3ed1-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="f3ed1-112">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f3ed1-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3ed1-113">O serviço desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3ed1-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f3ed1-114">ref</span><span class="sxs-lookup"><span data-stu-id="f3ed1-114">ref</span></span>  
 <span data-ttu-id="f3ed1-115">Tipo de dados: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="f3ed1-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="f3ed1-116">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="f3ed1-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="f3ed1-117">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f3ed1-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3ed1-118">Contém propriedades do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3ed1-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ed1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3ed1-119">Requirements</span></span>  
  
|<span data-ttu-id="f3ed1-120">MOF</span><span class="sxs-lookup"><span data-stu-id="f3ed1-120">MOF</span></span>|<span data-ttu-id="f3ed1-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f3ed1-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3ed1-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="f3ed1-122">Namespace</span></span>|<span data-ttu-id="f3ed1-123">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3ed1-123">Defined in root\ServiceModel</span></span>|
