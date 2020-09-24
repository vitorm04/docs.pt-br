---
title: Elemento <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 864a371d4ad10585e672452ad85cc09d4b684068
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158832"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="c8e51-102">Elemento \<enforceFIPSPolicy></span><span class="sxs-lookup"><span data-stu-id="c8e51-102">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="c8e51-103">Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).</span><span class="sxs-lookup"><span data-stu-id="c8e51-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="c8e51-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8e51-104">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8e51-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c8e51-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c8e51-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c8e51-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8e51-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8e51-107">Attributes</span></span>  
  
|<span data-ttu-id="c8e51-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c8e51-108">Attribute</span></span>|<span data-ttu-id="c8e51-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8e51-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8e51-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="c8e51-110">enabled</span></span>|<span data-ttu-id="c8e51-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c8e51-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c8e51-112">Especifica se é necessário habilitar a imposição de um requisito de configuração de computador que os algoritmos criptográficos devem ser compatíveis com o FIPS.</span><span class="sxs-lookup"><span data-stu-id="c8e51-112">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c8e51-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="c8e51-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="c8e51-114">Valor</span><span class="sxs-lookup"><span data-stu-id="c8e51-114">Value</span></span>|<span data-ttu-id="c8e51-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8e51-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c8e51-116">Se o computador estiver configurado para exigir que os algoritmos criptográficos sejam compatíveis com FIPS, esse requisito será imposto.</span><span class="sxs-lookup"><span data-stu-id="c8e51-116">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="c8e51-117">Se uma classe implementa um algoritmo que não está em conformidade com o FIPS, os construtores ou `Create` métodos dessa classe lançam exceções quando são executados nesse computador.</span><span class="sxs-lookup"><span data-stu-id="c8e51-117">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="c8e51-118">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c8e51-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="c8e51-119">Os algoritmos de criptografia usados pelo aplicativo não precisam ser compatíveis com o FIPS, independentemente da configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="c8e51-119">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8e51-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c8e51-120">Child Elements</span></span>  

 <span data-ttu-id="c8e51-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c8e51-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8e51-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c8e51-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c8e51-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8e51-123">Element</span></span>|<span data-ttu-id="c8e51-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8e51-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c8e51-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8e51-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c8e51-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c8e51-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8e51-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8e51-127">Remarks</span></span>  

 <span data-ttu-id="c8e51-128">A partir do .NET Framework 2,0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="c8e51-128">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="c8e51-129">Se o computador estiver configurado para exigir que os algoritmos sejam compatíveis com o FIPS e uma classe implementar um algoritmo que não seja compatível com o FIPS, qualquer tentativa de criar uma instância dessa classe gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c8e51-129">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="c8e51-130">Os construtores geram uma <xref:System.InvalidOperationException> exceção e os `Create` métodos geram uma exceção <xref:System.Reflection.TargetInvocationException> com uma <xref:System.InvalidOperationException> exceção interna.</span><span class="sxs-lookup"><span data-stu-id="c8e51-130">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="c8e51-131">Se seu aplicativo for executado em computadores cujas configurações exigem conformidade com o FIPS e seu aplicativo usa um algoritmo que não é compatível com o FIPS, você pode usar esse elemento em seu arquivo de configuração para impedir que o Common Language Runtime (CLR) imponha a conformidade com o FIPS.</span><span class="sxs-lookup"><span data-stu-id="c8e51-131">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="c8e51-132">Esse elemento foi introduzido no .NET Framework 2,0 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="c8e51-132">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e51-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8e51-133">Example</span></span>  

 <span data-ttu-id="c8e51-134">O exemplo a seguir mostra como impedir que o CLR imponha a conformidade com o FIPS.</span><span class="sxs-lookup"><span data-stu-id="c8e51-134">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8e51-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8e51-135">See also</span></span>

- [<span data-ttu-id="c8e51-136">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="c8e51-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c8e51-137">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c8e51-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c8e51-138">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="c8e51-138">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
