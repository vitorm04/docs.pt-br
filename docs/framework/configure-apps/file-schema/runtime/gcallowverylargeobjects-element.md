---
title: Elemento <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: b6230833808ec45d702502e36f929db4e03173e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116802"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="6dfd7-102">\<elemento de > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="6dfd7-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="6dfd7-103">Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="6dfd7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6dfd7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6dfd7-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="6dfd7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6dfd7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects >**</span><span class="sxs-lookup"><span data-stu-id="6dfd7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfd7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dfd7-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dfd7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6dfd7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6dfd7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dfd7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="6dfd7-110">Attributes</span></span>  
  
|<span data-ttu-id="6dfd7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="6dfd7-111">Attribute</span></span>|<span data-ttu-id="6dfd7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfd7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6dfd7-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6dfd7-114">Especifica se as matrizes maiores que 2 GB no tamanho total estão habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6dfd7-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="6dfd7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6dfd7-116">Valor</span><span class="sxs-lookup"><span data-stu-id="6dfd7-116">Value</span></span>|<span data-ttu-id="6dfd7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfd7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6dfd7-118">Matrizes maiores que 2 GB no tamanho total não estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="6dfd7-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6dfd7-120">Matrizes maiores que 2 GB no tamanho total são habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6dfd7-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6dfd7-121">Child Elements</span></span>  
 <span data-ttu-id="6dfd7-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6dfd7-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6dfd7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6dfd7-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="6dfd7-124">Element</span></span>|<span data-ttu-id="6dfd7-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfd7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6dfd7-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6dfd7-127">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dfd7-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="6dfd7-128">Remarks</span></span>  
 <span data-ttu-id="6dfd7-129">O uso desse elemento em seu arquivo de configuração de aplicativo permite que matrizes com mais de 2 GB de tamanho, mas não alteram outros limites no tamanho do objeto ou tamanho da matriz:</span><span class="sxs-lookup"><span data-stu-id="6dfd7-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="6dfd7-130">O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="6dfd7-131">O índice máximo em qualquer dimensão única é 2.147.483.591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único e 2.146.435.071 (0X7FEFFFFF) para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="6dfd7-132">O tamanho máximo para cadeias de caracteres e outros objetos que não são da matriz não são alterados.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="6dfd7-133">Antes de habilitar esse recurso, verifique se o seu aplicativo não inclui um código não seguro que assuma que todas as matrizes tenham menos de 2 GB de tamanho.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="6dfd7-134">Por exemplo, o código não seguro que usa matrizes como buffers pode ser suscetível a estouros de buffer se ele for escrito na suposição de que as matrizes não excederão 2 GB.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dfd7-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6dfd7-135">Example</span></span>  
 <span data-ttu-id="6dfd7-136">O exemplo a seguir mostra como habilitar esse recurso para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6dfd7-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="6dfd7-137">Com suporte em</span><span class="sxs-lookup"><span data-stu-id="6dfd7-137">Supported in</span></span>

<span data-ttu-id="6dfd7-138">.NET Framework 4,5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="6dfd7-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="6dfd7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dfd7-139">See also</span></span>

- [<span data-ttu-id="6dfd7-140">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="6dfd7-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6dfd7-141">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6dfd7-141">Configuration File Schema</span></span>](../index.md)
