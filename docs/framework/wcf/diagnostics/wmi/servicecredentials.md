---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572114"
---
# <a name="servicecredentials"></a><span data-ttu-id="80911-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="80911-102">ServiceCredentials</span></span>
<span data-ttu-id="80911-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="80911-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80911-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80911-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="80911-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="80911-105">Methods</span></span>  
 <span data-ttu-id="80911-106">A classe ServiceCredentials não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="80911-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="80911-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="80911-107">Properties</span></span>  
 <span data-ttu-id="80911-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="80911-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="80911-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="80911-109">ClientCertificate</span></span>  
 <span data-ttu-id="80911-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-110">Data type: string</span></span>  
  
 <span data-ttu-id="80911-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-112">Os certificado de autenticação e provisionamento configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="80911-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="80911-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="80911-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="80911-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-114">Data type: string</span></span>  
  
 <span data-ttu-id="80911-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="80911-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="80911-117">Par</span><span class="sxs-lookup"><span data-stu-id="80911-117">Peer</span></span>  
 <span data-ttu-id="80911-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-118">Data type: string</span></span>  
  
 <span data-ttu-id="80911-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="80911-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="80911-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="80911-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="80911-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-122">Data type: string</span></span>  
  
 <span data-ttu-id="80911-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="80911-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="80911-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="80911-125">ServiceCertificate</span></span>  
 <span data-ttu-id="80911-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-126">Data type: string</span></span>  
  
 <span data-ttu-id="80911-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="80911-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="80911-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="80911-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="80911-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-130">Data type: string</span></span>  
  
 <span data-ttu-id="80911-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-132">As configurações de nome de usuário e senha para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="80911-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="80911-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="80911-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="80911-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="80911-134">Data type: string</span></span>  
  
 <span data-ttu-id="80911-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="80911-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80911-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="80911-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80911-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80911-137">Requirements</span></span>  
  
|<span data-ttu-id="80911-138">MOF</span><span class="sxs-lookup"><span data-stu-id="80911-138">MOF</span></span>|<span data-ttu-id="80911-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="80911-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="80911-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="80911-140">Namespace</span></span>|<span data-ttu-id="80911-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="80911-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80911-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80911-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceCredentials>
