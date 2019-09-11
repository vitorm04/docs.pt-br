---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: b499294af71ba230dcf985d4af1d013b1ca260cf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850033"
---
# <a name="comcontract"></a><span data-ttu-id="ea50c-101">\<> de descontrato</span><span class="sxs-lookup"><span data-stu-id="ea50c-101">\<comContract></span></span>
<span data-ttu-id="ea50c-102">Especifica um contrato de serviço de integração COM+.</span><span class="sxs-lookup"><span data-stu-id="ea50c-102">Specifies a COM+ integration service contract.</span></span>  
  
<span data-ttu-id="ea50c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea50c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea50c-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea50c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ea50c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de com-contratos**](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="ea50c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="ea50c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de descontrato**</span><span class="sxs-lookup"><span data-stu-id="ea50c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea50c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea50c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea50c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea50c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea50c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ea50c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea50c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea50c-110">Attributes</span></span>  
  
|<span data-ttu-id="ea50c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ea50c-111">Attribute</span></span>|<span data-ttu-id="ea50c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea50c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea50c-113">contrato</span><span class="sxs-lookup"><span data-stu-id="ea50c-113">contract</span></span>|<span data-ttu-id="ea50c-114">Uma cadeia de caracteres que contém o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="ea50c-114">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="ea50c-115">name</span><span class="sxs-lookup"><span data-stu-id="ea50c-115">name</span></span>|<span data-ttu-id="ea50c-116">Uma cadeia de caracteres que contém o nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="ea50c-116">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="ea50c-117">namespace</span><span class="sxs-lookup"><span data-stu-id="ea50c-117">namespace</span></span>|<span data-ttu-id="ea50c-118">Uma cadeia de caracteres que contém o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="ea50c-118">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="ea50c-119">requiresSession</span><span class="sxs-lookup"><span data-stu-id="ea50c-119">requiresSession</span></span>|<span data-ttu-id="ea50c-120">Um valor booliano que especifica se o contrato só pode ser usado em associações de sessão.</span><span class="sxs-lookup"><span data-stu-id="ea50c-120">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="ea50c-121">Quando o serviço é inicializado, o Integration Runtime garante que essa configuração seja consistente com o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="ea50c-121">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="ea50c-122">Uma exceção será gerada se uma ou mais das associações para o contrato estiverem em conflito.</span><span class="sxs-lookup"><span data-stu-id="ea50c-122">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="ea50c-123">Se essa propriedade for `false`, e um canal unidirecional estiver em uso e houver quaisquer parâmetros [out], uma exceção também será gerada.</span><span class="sxs-lookup"><span data-stu-id="ea50c-123">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea50c-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ea50c-124">Child Elements</span></span>  
  
|<span data-ttu-id="ea50c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea50c-125">Element</span></span>|<span data-ttu-id="ea50c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea50c-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea50c-127">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="ea50c-127">persistableTypes</span></span>|<span data-ttu-id="ea50c-128">Todos os tipos persistentes.</span><span class="sxs-lookup"><span data-stu-id="ea50c-128">All the persistable types.</span></span>|  
|<span data-ttu-id="ea50c-129">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="ea50c-129">userDefinedTypes</span></span>|<span data-ttu-id="ea50c-130">Uma coleção de tipos definidos pelo usuário (UDT) que deve ser incluída no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ea50c-130">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="ea50c-131">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="ea50c-131">exposedMethods</span></span>|<span data-ttu-id="ea50c-132">Uma coleção de métodos COM+ que são expostos quando a interface em um componente COM+ é exposta como um serviço Web.</span><span class="sxs-lookup"><span data-stu-id="ea50c-132">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea50c-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ea50c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ea50c-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea50c-134">Element</span></span>|<span data-ttu-id="ea50c-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea50c-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea50c-136">comContracts</span><span class="sxs-lookup"><span data-stu-id="ea50c-136">comContracts</span></span>|<span data-ttu-id="ea50c-137">Contém uma coleção de `comContract` elementos.</span><span class="sxs-lookup"><span data-stu-id="ea50c-137">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea50c-138">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea50c-138">Remarks</span></span>  
 <span data-ttu-id="ea50c-139">Os contratos do serviço de `http://tempuri.org` integração com+ estão atualmente restritos ao namespace e o nome do contrato é derivado da interface com de suporte.</span><span class="sxs-lookup"><span data-stu-id="ea50c-139">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="ea50c-140">No entanto, você pode especificar alternativas usando a `comContracts` seção, bem como o `comContract` elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="ea50c-140">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="ea50c-141">Por exemplo, você pode usar a configuração a seguir para especificar o namespace, o nome do contrato e os tipos definidos pelo usuário a serem incluídos, bem como outras configurações para um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ea50c-141">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
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
  
 <span data-ttu-id="ea50c-142">Quando o serviço é inicializado, os namespaces e os nomes de contrato especificados são aplicados às descrições de serviço geradas.</span><span class="sxs-lookup"><span data-stu-id="ea50c-142">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea50c-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea50c-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [<span data-ttu-id="ea50c-144">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="ea50c-144">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="ea50c-145">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="ea50c-145">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="ea50c-146">Como: Definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="ea50c-146">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
