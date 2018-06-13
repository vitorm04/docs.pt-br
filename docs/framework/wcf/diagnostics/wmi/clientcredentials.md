---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: aa852ff82c44a3b5009dbc70e1067face44cbbe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486370"
---
# <a name="clientcredentials"></a><span data-ttu-id="a19d8-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a19d8-102">ClientCredentials</span></span>
<span data-ttu-id="a19d8-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a19d8-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a19d8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a19d8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a19d8-105">Methods</span></span>  
 <span data-ttu-id="a19d8-106">A classe ClientCredentials não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a19d8-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a19d8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a19d8-107">Properties</span></span>  
 <span data-ttu-id="a19d8-108">A classe ClientCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a19d8-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="a19d8-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a19d8-109">ClientCertificate</span></span>  
 <span data-ttu-id="a19d8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-110">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-112">O certificado x. 509 o cliente usa para autenticar no serviço.</span><span class="sxs-lookup"><span data-stu-id="a19d8-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="a19d8-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="a19d8-113">HttpDigest</span></span>  
 <span data-ttu-id="a19d8-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-114">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-116">A credencial resumida Http.</span><span class="sxs-lookup"><span data-stu-id="a19d8-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="a19d8-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="a19d8-117">IssuedToken</span></span>  
 <span data-ttu-id="a19d8-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-118">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-120">O endereço do ponto de extremidade e a associação usada para entrar em contato com o serviço de token de segurança local.</span><span class="sxs-lookup"><span data-stu-id="a19d8-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="a19d8-121">ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="a19d8-121">Peer</span></span>  
 <span data-ttu-id="a19d8-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-122">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-124">As credenciais que o nó par usa para se autenticar em outros nós da malha.</span><span class="sxs-lookup"><span data-stu-id="a19d8-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="a19d8-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="a19d8-125">ServiceCertificate</span></span>  
 <span data-ttu-id="a19d8-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-126">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-128">Certificado de x. 509 do serviço.</span><span class="sxs-lookup"><span data-stu-id="a19d8-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="a19d8-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="a19d8-129">SupportInteractive</span></span>  
 <span data-ttu-id="a19d8-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a19d8-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a19d8-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-132">Um valor booleano que especifica se a credencial oferece suporte à negociação interativa.</span><span class="sxs-lookup"><span data-stu-id="a19d8-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="a19d8-133">UserName</span><span class="sxs-lookup"><span data-stu-id="a19d8-133">UserName</span></span>  
 <span data-ttu-id="a19d8-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-134">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-136">O nome de usuário e a senha que o cliente usa para se autenticar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a19d8-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="a19d8-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a19d8-137">Windows</span></span>  
 <span data-ttu-id="a19d8-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a19d8-138">Data type: string</span></span>  
  
 <span data-ttu-id="a19d8-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a19d8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a19d8-140">As credenciais do windows a cliente usa para se autenticar para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a19d8-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a19d8-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a19d8-141">Requirements</span></span>  
  
|<span data-ttu-id="a19d8-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a19d8-142">MOF</span></span>|<span data-ttu-id="a19d8-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a19d8-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a19d8-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="a19d8-144">Namespace</span></span>|<span data-ttu-id="a19d8-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a19d8-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a19d8-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a19d8-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
