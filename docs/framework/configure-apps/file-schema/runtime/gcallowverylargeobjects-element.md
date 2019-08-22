---
title: Elemento <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6db26d250de191559fdae0479aca9f41c147502
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663707"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="ac77c-102">\<Elemento de > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="ac77c-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="ac77c-103">Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.</span><span class="sxs-lookup"><span data-stu-id="ac77c-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="ac77c-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="ac77c-104">\<configuration> Element</span></span>  
<span data-ttu-id="ac77c-105">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ac77c-105">\<runtime> Element</span></span>  
<span data-ttu-id="ac77c-106">\<Elemento de > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="ac77c-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac77c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac77c-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac77c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ac77c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ac77c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ac77c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac77c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ac77c-110">Attributes</span></span>  
  
|<span data-ttu-id="ac77c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ac77c-111">Attribute</span></span>|<span data-ttu-id="ac77c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac77c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ac77c-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ac77c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac77c-114">Especifica se as matrizes maiores que 2 GB no tamanho total estão habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ac77c-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ac77c-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ac77c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ac77c-116">Valor</span><span class="sxs-lookup"><span data-stu-id="ac77c-116">Value</span></span>|<span data-ttu-id="ac77c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac77c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ac77c-118">Matrizes maiores que 2 GB no tamanho total não estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="ac77c-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="ac77c-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ac77c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="ac77c-120">Matrizes maiores que 2 GB no tamanho total são habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ac77c-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac77c-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ac77c-121">Child Elements</span></span>  
 <span data-ttu-id="ac77c-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ac77c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac77c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ac77c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ac77c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="ac77c-124">Element</span></span>|<span data-ttu-id="ac77c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac77c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac77c-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ac77c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ac77c-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac77c-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac77c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="ac77c-128">Remarks</span></span>  
 <span data-ttu-id="ac77c-129">O uso desse elemento em seu arquivo de configuração de aplicativo permite que matrizes com mais de 2 GB de tamanho, mas não alteram outros limites no tamanho do objeto ou tamanho da matriz:</span><span class="sxs-lookup"><span data-stu-id="ac77c-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="ac77c-130">O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ac77c-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="ac77c-131">O índice máximo em qualquer dimensão única é 2.147.483.591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único e 2.146.435.071 (0X7FEFFFFF) para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="ac77c-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="ac77c-132">O tamanho máximo para cadeias de caracteres e outros objetos que não são da matriz não são alterados.</span><span class="sxs-lookup"><span data-stu-id="ac77c-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ac77c-133">Antes de habilitar esse recurso, verifique se o seu aplicativo não inclui um código não seguro que assuma que todas as matrizes tenham menos de 2 GB de tamanho.</span><span class="sxs-lookup"><span data-stu-id="ac77c-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="ac77c-134">Por exemplo, o código não seguro que usa matrizes como buffers pode ser suscetível a estouros de buffer se ele for escrito na suposição de que as matrizes não excederão 2 GB.</span><span class="sxs-lookup"><span data-stu-id="ac77c-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac77c-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ac77c-135">Example</span></span>  
 <span data-ttu-id="ac77c-136">O exemplo a seguir mostra como habilitar esse recurso para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ac77c-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="ac77c-137">Com suporte em</span><span class="sxs-lookup"><span data-stu-id="ac77c-137">Supported in</span></span>

<span data-ttu-id="ac77c-138">.NET Framework 4,5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ac77c-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="ac77c-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac77c-139">See also</span></span>

- [<span data-ttu-id="ac77c-140">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ac77c-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac77c-141">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="ac77c-141">Configuration File Schema</span></span>](../index.md)
