---
title: ServiceAppDomain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 325497435e24843cc74e804ef38e562617f27167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="serviceappdomain"></a><span data-ttu-id="808b3-102">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="808b3-102">ServiceAppDomain</span></span>
<span data-ttu-id="808b3-103">Um serviço é mapeado para um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="808b3-103">Maps a service to an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="808b3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="808b3-104">Syntax</span></span>  
  
```  
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="808b3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="808b3-105">Methods</span></span>  
 <span data-ttu-id="808b3-106">A classe ServiceAppDomain não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="808b3-106">The ServiceAppDomain class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="808b3-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="808b3-107">Properties</span></span>  
 <span data-ttu-id="808b3-108">A classe ServiceAppDomain tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="808b3-108">The ServiceAppDomain class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="808b3-109">ref</span><span class="sxs-lookup"><span data-stu-id="808b3-109">ref</span></span>  
 <span data-ttu-id="808b3-110">Tipo de dados: serviço</span><span class="sxs-lookup"><span data-stu-id="808b3-110">Data type: Service</span></span>  
<span data-ttu-id="808b3-111">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="808b3-111">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="808b3-112">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="808b3-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="808b3-113">O serviço desse domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="808b3-113">The service of this application domain.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="808b3-114">ref</span><span class="sxs-lookup"><span data-stu-id="808b3-114">ref</span></span>  
 <span data-ttu-id="808b3-115">Tipo de dados: AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="808b3-115">Data type: AppDomainInfo</span></span>  
<span data-ttu-id="808b3-116">Qualificadores: chave</span><span class="sxs-lookup"><span data-stu-id="808b3-116">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="808b3-117">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="808b3-117">Access type: Read-only</span></span>  
  
 <span data-ttu-id="808b3-118">Contém propriedades do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="808b3-118">Contains properties of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="808b3-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="808b3-119">Requirements</span></span>  
  
|<span data-ttu-id="808b3-120">MOF</span><span class="sxs-lookup"><span data-stu-id="808b3-120">MOF</span></span>|<span data-ttu-id="808b3-121">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="808b3-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="808b3-122">Namespace</span><span class="sxs-lookup"><span data-stu-id="808b3-122">Namespace</span></span>|<span data-ttu-id="808b3-123">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="808b3-123">Defined in root\ServiceModel</span></span>|
