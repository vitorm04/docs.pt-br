---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854839"
---
# \<userDefinedType>
<span data-ttu-id="89b24-101">Representa um tipo definido pelo usuário (UDT) que deve ser incluído no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="89b24-101">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a><span data-ttu-id="89b24-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89b24-102">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89b24-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="89b24-103">Attributes and Elements</span></span>  
 <span data-ttu-id="89b24-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="89b24-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89b24-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="89b24-105">Attributes</span></span>  
  
|<span data-ttu-id="89b24-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="89b24-106">Attribute</span></span>|<span data-ttu-id="89b24-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b24-107">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="89b24-108">Um atributo opcional que contém uma cadeia de caracteres que fornece o nome de tipo legível.</span><span class="sxs-lookup"><span data-stu-id="89b24-108">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="89b24-109">Isso não é usado pelo tempo de execução, mas ajuda um leitor a distinguir os tipos.</span><span class="sxs-lookup"><span data-stu-id="89b24-109">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="89b24-110">Uma cadeia de caracteres GUID que identifica o tipo UDT específico dentro da biblioteca de tipos registrada.</span><span class="sxs-lookup"><span data-stu-id="89b24-110">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="89b24-111">Uma cadeia de caracteres GUID que identifica a biblioteca de tipos registrada que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="89b24-111">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="89b24-112">Uma cadeia de caracteres que identifica a versão da biblioteca de tipos que define o tipo.</span><span class="sxs-lookup"><span data-stu-id="89b24-112">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89b24-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="89b24-113">Child Elements</span></span>  
 <span data-ttu-id="89b24-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="89b24-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89b24-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="89b24-115">Parent Elements</span></span>  
  
|<span data-ttu-id="89b24-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="89b24-116">Element</span></span>|<span data-ttu-id="89b24-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="89b24-117">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="89b24-118">Uma coleção de elementos `userDefinedType`.</span><span class="sxs-lookup"><span data-stu-id="89b24-118">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89b24-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="89b24-119">Remarks</span></span>  
 <span data-ttu-id="89b24-120">O Integration Runtime do COM+ cria serviços inspecionando a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="89b24-120">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="89b24-121">Quando um componente COM+ contém métodos que passam por uma variante, o sistema não pode determinar os tipos reais a serem passados antes do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89b24-121">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="89b24-122">Portanto, quando você tenta passar um UDT (tipo definido pelo usuário) em uma variante, ele falha porque não é um tipo conhecido para serialização.</span><span class="sxs-lookup"><span data-stu-id="89b24-122">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="89b24-123">Para evitar esse problema, você pode adicionar os UDTs ao arquivo de configuração para que eles possam ser incluídos como tipos conhecidos no contrato de serviço apropriado.</span><span class="sxs-lookup"><span data-stu-id="89b24-123">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="89b24-124">Para fazer isso, você precisa identificar exclusivamente o UDT e os contratos, ou seja, as interfaces COM originais que o usam....</span><span class="sxs-lookup"><span data-stu-id="89b24-124">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="89b24-125">O exemplo a seguir demonstra como adicionar dois UDTs específicos à `userDefinedTypes` seção <> do arquivo de configuração para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="89b24-125">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 <span data-ttu-id="89b24-126">Quando o serviço é inicializado, o Integration Runtime pesquisa os tipos especificados e os adiciona à coleção de tipos conhecidos para os contratos especificados.</span><span class="sxs-lookup"><span data-stu-id="89b24-126">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b24-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="89b24-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="89b24-128">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="89b24-128">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="89b24-129">Como configurar configurações de serviço de COM+</span><span class="sxs-lookup"><span data-stu-id="89b24-129">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
