---
title: "Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="93b24-102">Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="93b24-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="93b24-103">O <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> métodos fornecem sobrecargas que não aceitam quaisquer parâmetros.</span><span class="sxs-lookup"><span data-stu-id="93b24-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="93b24-104">Por padrão, essas sobrecargas sem parâmetros realizar alterações com base no valor da <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93b24-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93b24-105">Isso produz resultados diferencia maiusculas de minúsculas podem variar de acordo com a cultura.</span><span class="sxs-lookup"><span data-stu-id="93b24-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="93b24-106">Para tornar claro se você quer que as alterações casos ser sensíveis à cultura ou não levam em conta a cultura, você deve usar as sobrecargas desses métodos que exigem que você especificar explicitamente um `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93b24-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="93b24-107">Alterações de maiusculas sensíveis à cultura, especifique `CultureInfo.CurrentCulture` para o `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93b24-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="93b24-108">Alterações de maiusculas não levam em conta a cultura, especifique `CultureInfo.InvariantCulture` para o `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93b24-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="93b24-109">Em geral, cadeias de caracteres são convertidas em um caso padrão para habilitar a pesquisa mais fácil mais tarde.</span><span class="sxs-lookup"><span data-stu-id="93b24-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="93b24-110">Quando cadeias de caracteres são usadas dessa maneira, você deve especificar `CultureInfo.InvariantCulture` para o `culture` parâmetro, porque o valor de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> poderá alterar entre a hora em que o caso é alterado e a hora em que a pesquisa ocorre.</span><span class="sxs-lookup"><span data-stu-id="93b24-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="93b24-111">Se uma decisão de segurança é baseada em uma operação de alteração, a operação deve ser sem diferenciação de cultura para garantir que o resultado não é afetado pelo valor da `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="93b24-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="93b24-112">Consulte a seção "Cadeia de caracteres comparações que Use a cultura atual" o [práticas recomendadas para usar cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md) artigo para um exemplo que demonstra as operações de cadeia de caracteres como sensíveis à cultura pode produzir resultados inconsistentes.</span><span class="sxs-lookup"><span data-stu-id="93b24-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="93b24-113">Usando os Métodos String.ToUpper e String.ToLower</span><span class="sxs-lookup"><span data-stu-id="93b24-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="93b24-114">Para maior clareza do código, é recomendável que você sempre use sobrecargas do `String.ToUpper` e `String.ToLower` métodos que permitem que você especifique um `culture` parâmetro explicitamente.</span><span class="sxs-lookup"><span data-stu-id="93b24-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="93b24-115">Por exemplo, o código a seguir realiza uma pesquisa de identificador.</span><span class="sxs-lookup"><span data-stu-id="93b24-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="93b24-116">O `key.ToLower` operação sensíveis à cultura por padrão, mas esse comportamento não está claro de ler o código.</span><span class="sxs-lookup"><span data-stu-id="93b24-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="93b24-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="93b24-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="93b24-118">Se você quiser que o `key.ToLower` operação sem diferenciação de cultura, você deve alterar o exemplo anterior da seguinte forma para usar explicitamente o `CultureInfo.InvariantCulture` ao alterar o caso.</span><span class="sxs-lookup"><span data-stu-id="93b24-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="93b24-119">Usando os Métodos Char.ToUpper e Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="93b24-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="93b24-120">Embora o `Char.ToUpper` e `Char.ToLower` métodos têm as mesmas características como o `String.ToUpper` e `String.ToLower` métodos, somente culturas afetados são turco (Turquia) e Azerbaidjano (Azerbaijão, latino).</span><span class="sxs-lookup"><span data-stu-id="93b24-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="93b24-121">Essas são apenas duas culturas com diferenças de maiusculas e minúsculas do caractere único.</span><span class="sxs-lookup"><span data-stu-id="93b24-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="93b24-122">Para obter mais detalhes sobre esse mapeamento de maiusculas exclusivo, consulte a seção "Maiusculas e minúsculas" a <xref:System.String> tópico sobre a classe.</span><span class="sxs-lookup"><span data-stu-id="93b24-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="93b24-123">Para maior clareza do código e garantir resultados consistentes, é recomendável que você sempre use as sobrecargas desses métodos que permitem que você especifique explicitamente um `culture` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93b24-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b24-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93b24-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="93b24-125">Executando operações de cadeia de caracteres que não levam em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="93b24-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
