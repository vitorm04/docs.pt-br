---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957067"
---
# <a name="serviceappdomain"></a><span data-ttu-id="8e57e-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="8e57e-102">ServiceAppDomain</span></span>
<span data-ttu-id="8e57e-103">Mapeia um serviço para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e57e-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e57e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e57e-104">Syntax</span></span>  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8e57e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8e57e-105">Methods</span></span>  
 <span data-ttu-id="8e57e-106">A classe ServiceAppDomain não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8e57e-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e57e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8e57e-107">Properties</span></span>  
 <span data-ttu-id="8e57e-108">A classe ServiceAppDomain tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8e57e-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8e57e-109">ref</span><span class="sxs-lookup"><span data-stu-id="8e57e-109">ref</span></span>  
 <span data-ttu-id="8e57e-110">Tipo de dados: Serviço</span><span class="sxs-lookup"><span data-stu-id="8e57e-110">Data type: Service</span></span>  
<span data-ttu-id="8e57e-111">Qualificadores: Chave</span><span class="sxs-lookup"><span data-stu-id="8e57e-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="8e57e-112">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e57e-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e57e-113">O serviço desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e57e-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8e57e-114">ref</span><span class="sxs-lookup"><span data-stu-id="8e57e-114">ref</span></span>  
 <span data-ttu-id="8e57e-115">Tipo de dados: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="8e57e-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="8e57e-116">Qualificadores: Chave</span><span class="sxs-lookup"><span data-stu-id="8e57e-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="8e57e-117">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e57e-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e57e-118">Contém propriedades do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8e57e-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e57e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e57e-119">Requirements</span></span>  
  
|<span data-ttu-id="8e57e-120">MOF</span><span class="sxs-lookup"><span data-stu-id="8e57e-120">MOF</span></span>|<span data-ttu-id="8e57e-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8e57e-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8e57e-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="8e57e-122">Namespace</span></span>|<span data-ttu-id="8e57e-123">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8e57e-123">Defined in root\ServiceModel</span></span>|
