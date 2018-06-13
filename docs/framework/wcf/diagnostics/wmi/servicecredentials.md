---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bf906e09ae71d26f8e95877f1c545c0724d57b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485730"
---
# <a name="servicecredentials"></a><span data-ttu-id="60b2f-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="60b2f-102">ServiceCredentials</span></span>
<span data-ttu-id="60b2f-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="60b2f-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b2f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60b2f-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="60b2f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="60b2f-105">Methods</span></span>  
 <span data-ttu-id="60b2f-106">A classe ServiceCredentials não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="60b2f-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="60b2f-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="60b2f-107">Properties</span></span>  
 <span data-ttu-id="60b2f-108">A classe ServiceCredentials tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="60b2f-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="60b2f-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="60b2f-109">ClientCertificate</span></span>  
 <span data-ttu-id="60b2f-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-110">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-112">Os certificado de provisionamento e autenticação de configurações do cliente para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="60b2f-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="60b2f-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="60b2f-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="60b2f-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-114">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-116">Atual emitido configurações de autenticação de token para este serviço.</span><span class="sxs-lookup"><span data-stu-id="60b2f-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="60b2f-117">ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="60b2f-117">Peer</span></span>  
 <span data-ttu-id="60b2f-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-118">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-120">Configurações a serem usadas pelos pontos de extremidade de transporte de par de provisionamento e autenticação de credencial atual.</span><span class="sxs-lookup"><span data-stu-id="60b2f-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="60b2f-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="60b2f-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="60b2f-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-122">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-124">Especifica as configurações atuais de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="60b2f-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="60b2f-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="60b2f-125">ServiceCertificate</span></span>  
 <span data-ttu-id="60b2f-126">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-126">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-128">O certificado associado a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="60b2f-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="60b2f-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="60b2f-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="60b2f-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-130">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-132">As configurações de nome de usuário e senha para este serviço.</span><span class="sxs-lookup"><span data-stu-id="60b2f-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="60b2f-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="60b2f-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="60b2f-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="60b2f-134">Data type: string</span></span>  
  
 <span data-ttu-id="60b2f-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="60b2f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="60b2f-136">As configurações de autenticação do Windows para este serviço.</span><span class="sxs-lookup"><span data-stu-id="60b2f-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60b2f-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60b2f-137">Requirements</span></span>  
  
|<span data-ttu-id="60b2f-138">MOF</span><span class="sxs-lookup"><span data-stu-id="60b2f-138">MOF</span></span>|<span data-ttu-id="60b2f-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="60b2f-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="60b2f-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="60b2f-140">Namespace</span></span>|<span data-ttu-id="60b2f-141">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="60b2f-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60b2f-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60b2f-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
