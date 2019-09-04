---
title: Elemento <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b53dcd4db7e0ac1e9079e763b8ed76c1088e0e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252195"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="ca7f9-102">\<Elemento de > UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ca7f9-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="ca7f9-103">Determina se o Common Language Runtime calcula códigos de hash para cadeias de caracteres por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="ca7f9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca7f9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca7f9-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca7f9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ca7f9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm>**</span><span class="sxs-lookup"><span data-stu-id="ca7f9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7f9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca7f9-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca7f9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ca7f9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ca7f9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca7f9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="ca7f9-110">Attributes</span></span>  
  
|<span data-ttu-id="ca7f9-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="ca7f9-111">Attribute</span></span>|<span data-ttu-id="ca7f9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7f9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ca7f9-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca7f9-114">Especifica se os códigos de hash para cadeias de caracteres são calculados em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ca7f9-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="ca7f9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ca7f9-116">Valor</span><span class="sxs-lookup"><span data-stu-id="ca7f9-116">Value</span></span>|<span data-ttu-id="ca7f9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7f9-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="ca7f9-118">O Common Language Runtime não computa códigos hash para cadeias de caracteres por aplicativo; um único algoritmo é usado para calcular códigos de hash de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="ca7f9-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="ca7f9-120">O Common Language Runtime computa códigos de hash para cadeias de caracteres por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="ca7f9-121">Cadeias de caracteres idênticas em domínios de aplicativo diferentes e em processos diferentes terão códigos de hash diferentes.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ca7f9-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ca7f9-122">Child Elements</span></span>  
 <span data-ttu-id="ca7f9-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ca7f9-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ca7f9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ca7f9-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="ca7f9-125">Element</span></span>|<span data-ttu-id="ca7f9-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca7f9-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ca7f9-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ca7f9-128">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca7f9-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca7f9-129">Remarks</span></span>  
 <span data-ttu-id="ca7f9-130">Por padrão, a <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método usam um único algoritmo de hash que produz um código hash consistente entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="ca7f9-131">Isso é equivalente a definir o `enabled` atributo `<UseRandomizedStringHashAlgorithm>` do elemento como `0`.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="ca7f9-132">Esse é o algoritmo de hash usado no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="ca7f9-133">A <xref:System.StringComparer> classe e o <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> método também podem usar um algoritmo de hash diferente que computa códigos de hash em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="ca7f9-134">Como resultado, os códigos de hash para cadeias de caracteres equivalentes serão diferentes entre domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="ca7f9-135">Esse é um recurso opcional; para aproveitar isso, você deve definir o `enabled` atributo `<UseRandomizedStringHashAlgorithm>` do elemento como `1`.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="ca7f9-136">A pesquisa de cadeia de caracteres em uma tabela de hash normalmente é uma operação O (1).</span><span class="sxs-lookup"><span data-stu-id="ca7f9-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="ca7f9-137">No entanto, quando ocorre um grande número de colisões, a pesquisa pode se tornar uma operação O (n<sup>2</sup>).</span><span class="sxs-lookup"><span data-stu-id="ca7f9-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="ca7f9-138">Você pode usar o `<UseRandomizedStringHashAlgorithm>` elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que, por sua vez, limita o número de colisões em potencial, especialmente quando as chaves das quais os códigos de hash são calculados se baseiam na entrada de dados por usuários.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7f9-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca7f9-139">Example</span></span>  
 <span data-ttu-id="ca7f9-140">O exemplo a seguir define `DisplayString` uma classe que inclui uma constante de cadeia `s`de caracteres privada,, cujo valor é "esta é uma cadeia de caracteres".</span><span class="sxs-lookup"><span data-stu-id="ca7f9-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="ca7f9-141">Ele também inclui um `ShowStringHashCode` método que exibe o valor da cadeia de caracteres e seu código hash junto com o nome do domínio do aplicativo no qual o método está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="ca7f9-142">Quando você executa o exemplo sem fornecer um arquivo de configuração, ele exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="ca7f9-143">Observe que os códigos de hash para a cadeia de caracteres são idênticos nos dois domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="ca7f9-144">No entanto, se você adicionar o seguinte arquivo de configuração ao diretório do exemplo e, em seguida, executar o exemplo, os códigos de hash para a mesma cadeia de caracteres serão diferentes pelo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca7f9-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ca7f9-145">Quando o arquivo de configuração estiver presente, o exemplo exibirá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ca7f9-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca7f9-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca7f9-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
