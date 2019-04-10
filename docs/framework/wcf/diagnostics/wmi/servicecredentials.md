---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230922"
---
# <a name="servicecredentials"></a><span data-ttu-id="be4ea-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="be4ea-102">ServiceCredentials</span></span>
<span data-ttu-id="be4ea-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="be4ea-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be4ea-104">Syntax</span></span>  
  
```csharp
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="be4ea-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="be4ea-105">Methods</span></span>  
 <span data-ttu-id="be4ea-106">A classe ServiceCredentials não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="be4ea-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="be4ea-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="be4ea-107">Properties</span></span>  
 <span data-ttu-id="be4ea-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="be4ea-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="be4ea-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="be4ea-109">ClientCertificate</span></span>  
 <span data-ttu-id="be4ea-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-110">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-112">Os certificado de autenticação e provisionamento configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="be4ea-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="be4ea-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="be4ea-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="be4ea-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-114">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="be4ea-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="be4ea-117">Par</span><span class="sxs-lookup"><span data-stu-id="be4ea-117">Peer</span></span>  
 <span data-ttu-id="be4ea-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-118">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="be4ea-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="be4ea-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="be4ea-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="be4ea-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-122">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="be4ea-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="be4ea-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="be4ea-125">ServiceCertificate</span></span>  
 <span data-ttu-id="be4ea-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-126">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="be4ea-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="be4ea-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="be4ea-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="be4ea-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-130">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-132">As configurações de nome de usuário e senha para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="be4ea-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="be4ea-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="be4ea-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="be4ea-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="be4ea-134">Data type: string</span></span>  
  
 <span data-ttu-id="be4ea-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="be4ea-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be4ea-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="be4ea-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4ea-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be4ea-137">Requirements</span></span>  
  
|<span data-ttu-id="be4ea-138">MOF</span><span class="sxs-lookup"><span data-stu-id="be4ea-138">MOF</span></span>|<span data-ttu-id="be4ea-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="be4ea-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="be4ea-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="be4ea-140">Namespace</span></span>|<span data-ttu-id="be4ea-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be4ea-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be4ea-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be4ea-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
