---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956971"
---
# <a name="servicecredentials"></a><span data-ttu-id="f83ac-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="f83ac-102">ServiceCredentials</span></span>
<span data-ttu-id="f83ac-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="f83ac-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f83ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f83ac-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f83ac-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f83ac-105">Methods</span></span>  
 <span data-ttu-id="f83ac-106">A classe ServiceCredentials não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="f83ac-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f83ac-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f83ac-107">Properties</span></span>  
 <span data-ttu-id="f83ac-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="f83ac-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="f83ac-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="f83ac-109">ClientCertificate</span></span>  
 <span data-ttu-id="f83ac-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-110">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-112">Os certificado de autenticação e provisionamento configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="f83ac-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="f83ac-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="f83ac-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="f83ac-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-114">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="f83ac-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="f83ac-117">Par</span><span class="sxs-lookup"><span data-stu-id="f83ac-117">Peer</span></span>  
 <span data-ttu-id="f83ac-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-118">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="f83ac-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="f83ac-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="f83ac-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="f83ac-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-122">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="f83ac-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="f83ac-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="f83ac-125">ServiceCertificate</span></span>  
 <span data-ttu-id="f83ac-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-126">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="f83ac-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="f83ac-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="f83ac-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="f83ac-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-130">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-132">As configurações de nome de usuário e senha para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="f83ac-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="f83ac-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="f83ac-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="f83ac-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f83ac-134">Data type: string</span></span>  
  
 <span data-ttu-id="f83ac-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="f83ac-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f83ac-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="f83ac-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f83ac-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f83ac-137">Requirements</span></span>  
  
|<span data-ttu-id="f83ac-138">MOF</span><span class="sxs-lookup"><span data-stu-id="f83ac-138">MOF</span></span>|<span data-ttu-id="f83ac-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f83ac-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f83ac-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="f83ac-140">Namespace</span></span>|<span data-ttu-id="f83ac-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f83ac-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f83ac-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f83ac-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
