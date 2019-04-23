---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772096"
---
# <a name="servicecredentials"></a><span data-ttu-id="4c80e-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4c80e-102">ServiceCredentials</span></span>
<span data-ttu-id="4c80e-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4c80e-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c80e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4c80e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4c80e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4c80e-105">Methods</span></span>  
 <span data-ttu-id="4c80e-106">A classe ServiceCredentials não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="4c80e-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4c80e-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4c80e-107">Properties</span></span>  
 <span data-ttu-id="4c80e-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4c80e-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="4c80e-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="4c80e-109">ClientCertificate</span></span>  
 <span data-ttu-id="4c80e-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-110">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-112">Os certificado de autenticação e provisionamento configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="4c80e-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="4c80e-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="4c80e-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="4c80e-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-114">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="4c80e-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="4c80e-117">Par</span><span class="sxs-lookup"><span data-stu-id="4c80e-117">Peer</span></span>  
 <span data-ttu-id="4c80e-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-118">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="4c80e-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="4c80e-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="4c80e-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="4c80e-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-122">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="4c80e-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="4c80e-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="4c80e-125">ServiceCertificate</span></span>  
 <span data-ttu-id="4c80e-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-126">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="4c80e-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="4c80e-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="4c80e-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="4c80e-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-130">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-132">As configurações de nome de usuário e senha para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="4c80e-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="4c80e-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="4c80e-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="4c80e-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4c80e-134">Data type: string</span></span>  
  
 <span data-ttu-id="4c80e-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4c80e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4c80e-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="4c80e-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c80e-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4c80e-137">Requirements</span></span>  
  
|<span data-ttu-id="4c80e-138">MOF</span><span class="sxs-lookup"><span data-stu-id="4c80e-138">MOF</span></span>|<span data-ttu-id="4c80e-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4c80e-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4c80e-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="4c80e-140">Namespace</span></span>|<span data-ttu-id="4c80e-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4c80e-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c80e-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c80e-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
