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
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153771"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="a8e89-102">\<UseRandomizedizedStringHashAlgorithm> Element</span><span class="sxs-lookup"><span data-stu-id="a8e89-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="a8e89-103">Determina se o tempo de execução do idioma comum calcula códigos hash para strings em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="a8e89-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8e89-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8e89-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8e89-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a8e89-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedizedStringHashAlgorithm>**</span><span class="sxs-lookup"><span data-stu-id="a8e89-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e89-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8e89-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8e89-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8e89-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a8e89-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a8e89-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8e89-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8e89-110">Attributes</span></span>  
  
|<span data-ttu-id="a8e89-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8e89-111">Attribute</span></span>|<span data-ttu-id="a8e89-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8e89-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a8e89-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a8e89-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a8e89-114">Especifica se os códigos hash para strings são calculados em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a8e89-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="a8e89-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a8e89-116">Valor</span><span class="sxs-lookup"><span data-stu-id="a8e89-116">Value</span></span>|<span data-ttu-id="a8e89-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8e89-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="a8e89-118">O tempo de execução do idioma comum não computa códigos hash para strings em uma base de domínio por aplicativo; um único algoritmo é usado para calcular códigos de hash de seqüência.</span><span class="sxs-lookup"><span data-stu-id="a8e89-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="a8e89-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="a8e89-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="a8e89-120">O tempo de execução do idioma comum calcula códigos hash para strings em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="a8e89-121">As strings idênticas em diferentes domínios de aplicativos e em diferentes processos terão diferentes códigos de hash.</span><span class="sxs-lookup"><span data-stu-id="a8e89-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8e89-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8e89-122">Child Elements</span></span>  
 <span data-ttu-id="a8e89-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8e89-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8e89-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8e89-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a8e89-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8e89-125">Element</span></span>|<span data-ttu-id="a8e89-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8e89-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a8e89-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8e89-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a8e89-128">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="a8e89-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8e89-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8e89-129">Remarks</span></span>  
 <span data-ttu-id="a8e89-130">Por padrão, <xref:System.StringComparer> a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> classe e o método usam um único algoritmo de hashing que produz um código de hash consistente entre os domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="a8e89-131">Isso equivale a `enabled` definir o `<UseRandomizedStringHashAlgorithm>` atributo do elemento para `0`.</span><span class="sxs-lookup"><span data-stu-id="a8e89-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="a8e89-132">Este é o algoritmo de hash usado no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a8e89-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="a8e89-133">A <xref:System.StringComparer> classe <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> e o método também podem usar um algoritmo de hash diferente que calcula códigos de hash em uma base de domínio por aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="a8e89-134">Como resultado, os códigos hash para strings equivalentes diferem entre os domínios do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="a8e89-135">Este é um recurso de opt-in; para tirar proveito disso, você `enabled` deve `<UseRandomizedStringHashAlgorithm>` definir `1`o atributo do elemento para .</span><span class="sxs-lookup"><span data-stu-id="a8e89-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="a8e89-136">A aparência de string em uma tabela hash é tipicamente uma operação O(1).</span><span class="sxs-lookup"><span data-stu-id="a8e89-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="a8e89-137">No entanto, quando um grande número de colisões ocorrem, a procuração pode se tornar uma operação O(n<sup>2).</sup></span><span class="sxs-lookup"><span data-stu-id="a8e89-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="a8e89-138">Você pode `<UseRandomizedStringHashAlgorithm>` usar o elemento de configuração para gerar um algoritmo de hash aleatório por domínio de aplicativo, que por sua vez limita o número de colisões potenciais, particularmente quando as chaves das quais os códigos de hash são calculados são baseadas na entrada de dados pelos usuários.</span><span class="sxs-lookup"><span data-stu-id="a8e89-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8e89-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8e89-139">Example</span></span>  
 <span data-ttu-id="a8e89-140">O exemplo a `DisplayString` seguir define uma classe que `s`inclui uma constante de string privada, cujo valor é "Isso é uma string".</span><span class="sxs-lookup"><span data-stu-id="a8e89-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="a8e89-141">Também inclui um método `ShowStringHashCode` que exibe o valor de cadeia de caracteres e seu código de hash com o nome do domínio do aplicativo no qual o método está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="a8e89-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="a8e89-142">Quando você executa o exemplo sem fornecer um arquivo de configuração, ele exibe uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="a8e89-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="a8e89-143">Observe que os códigos hash para a cadeia de caracteres são idênticos nos dois domínios de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="a8e89-144">Entretanto, se você adicionar o seguinte arquivo de configuração ao diretório de exemplo e, então, executar o exemplo, os códigos hash da mesma cadeia de caracteres diferirão de acordo com o domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8e89-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a8e89-145">Quando o arquivo de configuração estiver presente, o exemplo exibe a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="a8e89-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8e89-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8e89-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
