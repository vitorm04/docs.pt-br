---
title: '&lt;userDefinedType&gt;'
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: ffa9480312c278097ae110c686fb507209c117e1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltuserdefinedtypegt"></a><span data-ttu-id="4a870-102">&lt;userDefinedType&gt;</span><span class="sxs-lookup"><span data-stu-id="4a870-102">&lt;userDefinedType&gt;</span></span>
<span data-ttu-id="4a870-103">Representa um tipo definido pelo usuário (UDT) que deve ser incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="4a870-103">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="4a870-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a870-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a870-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4a870-105">\<comContracts></span></span>  
<span data-ttu-id="4a870-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="4a870-106">\<comContract></span></span>  
<span data-ttu-id="4a870-107">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="4a870-107">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a870-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a870-108">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a870-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a870-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a870-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a870-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a870-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a870-111">Attributes</span></span>  
  
|<span data-ttu-id="4a870-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="4a870-112">Attribute</span></span>|<span data-ttu-id="4a870-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a870-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4a870-114">Um atributo opcional que contém uma cadeia de caracteres que fornece o nome de tipo legível.</span><span class="sxs-lookup"><span data-stu-id="4a870-114">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="4a870-115">Isso não é usado pelo tempo de execução, mas ajuda a um leitor para distinguir os tipos.</span><span class="sxs-lookup"><span data-stu-id="4a870-115">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="4a870-116">Uma cadeia de caracteres GUID que identifica o tipo UDT específico dentro da biblioteca de tipos registrada.</span><span class="sxs-lookup"><span data-stu-id="4a870-116">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="4a870-117">Uma cadeia de caracteres GUID que identifica a biblioteca de tipos registrada que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="4a870-117">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="4a870-118">Uma cadeia de caracteres que identifica a versão da biblioteca de tipo que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="4a870-118">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a870-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a870-119">Child Elements</span></span>  
 <span data-ttu-id="4a870-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4a870-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a870-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a870-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4a870-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a870-122">Element</span></span>|<span data-ttu-id="4a870-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a870-123">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="4a870-124">Uma coleção de elementos `userDefinedType`.</span><span class="sxs-lookup"><span data-stu-id="4a870-124">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a870-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a870-125">Remarks</span></span>  
 <span data-ttu-id="4a870-126">O tempo de execução de integração COM+ cria serviços inspecionando a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="4a870-126">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="4a870-127">Quando um componente COM+ contém métodos que passam um tipo VARIANT, o sistema não pode determinar os tipos reais a serem passados antes do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4a870-127">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="4a870-128">Portanto, quando você tentar passar um usuário definido pelo tipo (UDT) dentro de um tipo VARIANT, ele falha porque não é um tipo conhecido para serialização.</span><span class="sxs-lookup"><span data-stu-id="4a870-128">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="4a870-129">Para contornar esse problema, você pode adicionar os UDTs para o arquivo de configuração para que eles podem ser incluídos como tipos conhecidos no contrato de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="4a870-129">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="4a870-130">Para fazer isso, você precisa identificar exclusivamente o UDT e o contrato (s), ou seja, as COM interfaces originais que utiliza.</span><span class="sxs-lookup"><span data-stu-id="4a870-130">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="4a870-131">O exemplo a seguir demonstra como adicionar dois UDTs específicos para o <`userDefinedTypes`> seção do arquivo de configuração para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="4a870-131">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="4a870-132">Quando o serviço é inicializado, o tempo de execução de integração procura os tipos especificados e os adiciona à coleção de tipos conhecidos para contratos especificados.</span><span class="sxs-lookup"><span data-stu-id="4a870-132">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a870-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a870-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [<span data-ttu-id="4a870-134">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="4a870-134">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="4a870-135">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="4a870-135">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="4a870-136">Como definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="4a870-136">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
