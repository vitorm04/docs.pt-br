---
title: Elemento <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154121"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="90919-102">\<gcAllowVeryLargeObjects> Element</span><span class="sxs-lookup"><span data-stu-id="90919-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="90919-103">Em plataformas de 64 bits, habilita matrizes com mais de 2 gigabytes (GB) de tamanho total.</span><span class="sxs-lookup"><span data-stu-id="90919-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="90919-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="90919-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="90919-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="90919-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="90919-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span><span class="sxs-lookup"><span data-stu-id="90919-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90919-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90919-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90919-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90919-108">Attributes and Elements</span></span>  
 <span data-ttu-id="90919-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="90919-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90919-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="90919-110">Attributes</span></span>  
  
|<span data-ttu-id="90919-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="90919-111">Attribute</span></span>|<span data-ttu-id="90919-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="90919-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="90919-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="90919-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="90919-114">Especifica se os arrays com maior duração de 2 GB no tamanho total estão habilitados em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="90919-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="90919-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="90919-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="90919-116">Valor</span><span class="sxs-lookup"><span data-stu-id="90919-116">Value</span></span>|<span data-ttu-id="90919-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="90919-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="90919-118">Matrizes maiores que 2 GB em tamanho total não estão habilitadas.</span><span class="sxs-lookup"><span data-stu-id="90919-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="90919-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="90919-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="90919-120">Matrizes maiores que 2 GB em tamanho total são habilitadas em plataformas de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="90919-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90919-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="90919-121">Child Elements</span></span>  
 <span data-ttu-id="90919-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="90919-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90919-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="90919-123">Parent Elements</span></span>  
  
|<span data-ttu-id="90919-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="90919-124">Element</span></span>|<span data-ttu-id="90919-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="90919-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="90919-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90919-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="90919-127">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="90919-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90919-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="90919-128">Remarks</span></span>  
 <span data-ttu-id="90919-129">O uso desse elemento no arquivo de configuração do aplicativo permite matrizes com tamanho superior a 2 GB, mas não altera outros limites no tamanho do objeto ou tamanho do array:</span><span class="sxs-lookup"><span data-stu-id="90919-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="90919-130">O número máximo de elementos em uma matriz é <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90919-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="90919-131">O índice máximo em qualquer dimensão é de 2.147.483.591 (0x7FFFFFC7) para matrizes de bytes e matrizes de estruturas de byte único, e 2.146.435.071 (0X7FEFFFFF) para outros tipos.</span><span class="sxs-lookup"><span data-stu-id="90919-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="90919-132">O tamanho máximo para strings e outros objetos não-array é inalterado.</span><span class="sxs-lookup"><span data-stu-id="90919-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="90919-133">Antes de habilitar esse recurso, certifique-se de que seu aplicativo não inclua código inseguro que pressupõe que todas as matrizes sejam menores que 2 GB de tamanho.</span><span class="sxs-lookup"><span data-stu-id="90919-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="90919-134">Por exemplo, o código inseguro que usa arrays como buffers pode ser suscetível a buffer saqueados se for escrito na suposição de que os arrays não excederão 2 GB.</span><span class="sxs-lookup"><span data-stu-id="90919-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90919-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90919-135">Example</span></span>  
 <span data-ttu-id="90919-136">O exemplo a seguir mostra como ativar esse recurso para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="90919-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="90919-137">Com suporte em</span><span class="sxs-lookup"><span data-stu-id="90919-137">Supported in</span></span>

<span data-ttu-id="90919-138">.NET Framework 4.5 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="90919-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="90919-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="90919-139">See also</span></span>

- [<span data-ttu-id="90919-140">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="90919-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="90919-141">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="90919-141">Configuration File Schema</span></span>](../index.md)
