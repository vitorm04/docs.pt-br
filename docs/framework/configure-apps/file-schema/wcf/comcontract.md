---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 8694f83a731363f83cb09de43214eb4b211ef5ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145061"
---
# <a name="comcontract"></a><span data-ttu-id="eb4de-101">\<comContract></span><span class="sxs-lookup"><span data-stu-id="eb4de-101">\<comContract></span></span>
<span data-ttu-id="eb4de-102">Especifica um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="eb4de-102">Specifies a COM+ integration service contract.</span></span>  
  
 <span data-ttu-id="eb4de-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb4de-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb4de-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="eb4de-104">\<comContracts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4de-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb4de-105">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb4de-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eb4de-106">Attributes and Elements</span></span>  
 <span data-ttu-id="eb4de-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eb4de-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb4de-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="eb4de-108">Attributes</span></span>  
  
|<span data-ttu-id="eb4de-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="eb4de-109">Attribute</span></span>|<span data-ttu-id="eb4de-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb4de-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb4de-111">contrato</span><span class="sxs-lookup"><span data-stu-id="eb4de-111">contract</span></span>|<span data-ttu-id="eb4de-112">Uma cadeia de caracteres que contém o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="eb4de-112">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="eb4de-113">name</span><span class="sxs-lookup"><span data-stu-id="eb4de-113">name</span></span>|<span data-ttu-id="eb4de-114">Uma cadeia de caracteres que contém o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="eb4de-114">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="eb4de-115">namespace</span><span class="sxs-lookup"><span data-stu-id="eb4de-115">namespace</span></span>|<span data-ttu-id="eb4de-116">Uma cadeia de caracteres que contém o namespace de contrato.</span><span class="sxs-lookup"><span data-stu-id="eb4de-116">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="eb4de-117">requiresSession</span><span class="sxs-lookup"><span data-stu-id="eb4de-117">requiresSession</span></span>|<span data-ttu-id="eb4de-118">Um valor booliano que especifica se o contrato só pode ser usado em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="eb4de-118">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="eb4de-119">Quando o serviço é inicializado, o integration runtime garante que essa configuração é consistente com o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="eb4de-119">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="eb4de-120">Uma exceção será gerada se um ou mais das associações para o contrato estão em conflito.</span><span class="sxs-lookup"><span data-stu-id="eb4de-120">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="eb4de-121">Se essa propriedade for `false`e um canal unidirecional está em uso e houver [parâmetros out], também será gerada uma exceção.</span><span class="sxs-lookup"><span data-stu-id="eb4de-121">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb4de-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eb4de-122">Child Elements</span></span>  
  
|<span data-ttu-id="eb4de-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb4de-123">Element</span></span>|<span data-ttu-id="eb4de-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb4de-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb4de-125">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="eb4de-125">persistableTypes</span></span>|<span data-ttu-id="eb4de-126">Todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="eb4de-126">All the persistable types.</span></span>|  
|<span data-ttu-id="eb4de-127">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="eb4de-127">userDefinedTypes</span></span>|<span data-ttu-id="eb4de-128">Uma coleção de usuário definidos UDTS (tipos) que deve ser incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb4de-128">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="eb4de-129">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="eb4de-129">exposedMethods</span></span>|<span data-ttu-id="eb4de-130">Uma coleção de métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="eb4de-130">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb4de-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eb4de-131">Parent Elements</span></span>  
  
|<span data-ttu-id="eb4de-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="eb4de-132">Element</span></span>|<span data-ttu-id="eb4de-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb4de-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eb4de-134">comContracts</span><span class="sxs-lookup"><span data-stu-id="eb4de-134">comContracts</span></span>|<span data-ttu-id="eb4de-135">Contém uma coleção de `comContract` elementos.</span><span class="sxs-lookup"><span data-stu-id="eb4de-135">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb4de-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb4de-136">Remarks</span></span>  
 <span data-ttu-id="eb4de-137">Contratos de serviço de integração COM+ são atualmente restritos ao `http://tempuri.org` namespace, e o nome do contrato é derivado da interface COM suporte.</span><span class="sxs-lookup"><span data-stu-id="eb4de-137">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="eb4de-138">No entanto, você pode especificar alternativas usando o `comContracts` seção, bem como o `comContract` elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="eb4de-138">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="eb4de-139">Por exemplo, você pode usar a configuração a seguir para especificar o namespace, nome do contrato e tipos definidos pelo usuário a serem incluídos, bem como outras configurações para um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="eb4de-139">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="eb4de-140">Quando o serviço é inicializado, os namespaces especificados e os nomes de contrato são aplicados as descrições de serviço gerado.</span><span class="sxs-lookup"><span data-stu-id="eb4de-140">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4de-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb4de-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="eb4de-142">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="eb4de-142">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="eb4de-143">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="eb4de-143">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="eb4de-144">Como: Definir as configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="eb4de-144">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
