---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6fba00dc98f6b5525e1cb9588ed52bc483a665e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="915e2-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="915e2-102">ClientCredentials</span></span>
<span data-ttu-id="915e2-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="915e2-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="915e2-104">Syntax</span></span>  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="915e2-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="915e2-105">Methods</span></span>  
 <span data-ttu-id="915e2-106">A classe ClientCredentials não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="915e2-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="915e2-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="915e2-107">Properties</span></span>  
 <span data-ttu-id="915e2-108">A classe ClientCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="915e2-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="915e2-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="915e2-109">ClientCertificate</span></span>  
 <span data-ttu-id="915e2-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-110">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-112">O certificado x. 509 o cliente usa para autenticar no serviço.</span><span class="sxs-lookup"><span data-stu-id="915e2-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="915e2-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="915e2-113">HttpDigest</span></span>  
 <span data-ttu-id="915e2-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-114">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-116">A credencial resumida Http.</span><span class="sxs-lookup"><span data-stu-id="915e2-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="915e2-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="915e2-117">IssuedToken</span></span>  
 <span data-ttu-id="915e2-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-118">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-120">O endereço do ponto de extremidade e a associação usada para entrar em contato com o serviço de token de segurança local.</span><span class="sxs-lookup"><span data-stu-id="915e2-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="915e2-121">ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="915e2-121">Peer</span></span>  
 <span data-ttu-id="915e2-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-122">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-124">As credenciais que o nó par usa para se autenticar em outros nós da malha.</span><span class="sxs-lookup"><span data-stu-id="915e2-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="915e2-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="915e2-125">ServiceCertificate</span></span>  
 <span data-ttu-id="915e2-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-126">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-128">Certificado de x. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="915e2-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="915e2-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="915e2-129">SupportInteractive</span></span>  
 <span data-ttu-id="915e2-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="915e2-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="915e2-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-132">Um valor booleano que especifica se a credencial oferece suporte à negociação interativa.</span><span class="sxs-lookup"><span data-stu-id="915e2-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="915e2-133">UserName</span><span class="sxs-lookup"><span data-stu-id="915e2-133">UserName</span></span>  
 <span data-ttu-id="915e2-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-134">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-136">O nome de usuário e a senha que o cliente usa para se autenticar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="915e2-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="915e2-137">Windows</span><span class="sxs-lookup"><span data-stu-id="915e2-137">Windows</span></span>  
 <span data-ttu-id="915e2-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="915e2-138">Data type: string</span></span>  
  
 <span data-ttu-id="915e2-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="915e2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="915e2-140">As credenciais do windows a cliente usa para se autenticar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="915e2-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915e2-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="915e2-141">Requirements</span></span>  
  
|<span data-ttu-id="915e2-142">MOF</span><span class="sxs-lookup"><span data-stu-id="915e2-142">MOF</span></span>|<span data-ttu-id="915e2-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="915e2-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="915e2-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="915e2-144">Namespace</span></span>|<span data-ttu-id="915e2-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="915e2-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="915e2-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="915e2-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
