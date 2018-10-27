---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: 8b6200f84f352d49cf142d9c8b97d1c2b36149b2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180894"
---
# <a name="clientcredentials"></a><span data-ttu-id="797a8-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="797a8-102">ClientCredentials</span></span>
<span data-ttu-id="797a8-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="797a8-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="797a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="797a8-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="797a8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="797a8-105">Methods</span></span>  
 <span data-ttu-id="797a8-106">A classe ClientCredentials não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="797a8-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="797a8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="797a8-107">Properties</span></span>  
 <span data-ttu-id="797a8-108">A classe ClientCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="797a8-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="797a8-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="797a8-109">ClientCertificate</span></span>  
 <span data-ttu-id="797a8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-110">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-112">O certificado x. 509 o cliente usa para se autenticar no serviço.</span><span class="sxs-lookup"><span data-stu-id="797a8-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="797a8-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="797a8-113">HttpDigest</span></span>  
 <span data-ttu-id="797a8-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-114">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-116">A credencial resumida Http atual.</span><span class="sxs-lookup"><span data-stu-id="797a8-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="797a8-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="797a8-117">IssuedToken</span></span>  
 <span data-ttu-id="797a8-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-118">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-120">O endereço de ponto de extremidade e associação usado para contatar o serviço de token de segurança local.</span><span class="sxs-lookup"><span data-stu-id="797a8-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="797a8-121">Par</span><span class="sxs-lookup"><span data-stu-id="797a8-121">Peer</span></span>  
 <span data-ttu-id="797a8-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-122">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-124">As credenciais que o nó par usa para se autenticar em outros nós na malha.</span><span class="sxs-lookup"><span data-stu-id="797a8-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="797a8-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="797a8-125">ServiceCertificate</span></span>  
 <span data-ttu-id="797a8-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-126">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-128">O certificado do serviço x. 509.</span><span class="sxs-lookup"><span data-stu-id="797a8-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="797a8-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="797a8-129">SupportInteractive</span></span>  
 <span data-ttu-id="797a8-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="797a8-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="797a8-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-132">Um valor booliano que especifica se a credencial dá suporte à negociação interativa.</span><span class="sxs-lookup"><span data-stu-id="797a8-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="797a8-133">UserName</span><span class="sxs-lookup"><span data-stu-id="797a8-133">UserName</span></span>  
 <span data-ttu-id="797a8-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-134">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-136">O nome de usuário e a senha que o cliente usa para autenticar-se com o serviço.</span><span class="sxs-lookup"><span data-stu-id="797a8-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="797a8-137">Windows</span><span class="sxs-lookup"><span data-stu-id="797a8-137">Windows</span></span>  
 <span data-ttu-id="797a8-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="797a8-138">Data type: string</span></span>  
  
 <span data-ttu-id="797a8-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="797a8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="797a8-140">O cliente usa para se autenticar para o serviço de credenciais do windows.</span><span class="sxs-lookup"><span data-stu-id="797a8-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="797a8-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="797a8-141">Requirements</span></span>  
  
|<span data-ttu-id="797a8-142">MOF</span><span class="sxs-lookup"><span data-stu-id="797a8-142">MOF</span></span>|<span data-ttu-id="797a8-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="797a8-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="797a8-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="797a8-144">Namespace</span></span>|<span data-ttu-id="797a8-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="797a8-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="797a8-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="797a8-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
