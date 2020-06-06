---
title: Referência do arquivo de configuração de diretivas do runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "76738415"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="fb14b-102">Referência do arquivo de configuração de diretivas do runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="fb14b-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="fb14b-103">O arquivo de diretivas de runtime (. rd.xml) é um arquivo de configuração XML que especifica se os elementos do programa designado estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="fb14b-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="fb14b-104">Aqui está um exemplo de um arquivo de diretivas de runtime:</span><span class="sxs-lookup"><span data-stu-id="fb14b-104">Here’s an example of a runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
    <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
    <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
    <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

    <Namespace Name="System.Collections.ObjectModel" >
      <TypeInstantiation Name="ObservableCollection"
            Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
      <TypeInstantiation Name="ReadOnlyObservableCollection"
            Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
    </Namespace>
  </Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="fb14b-105">A estrutura de um arquivo de diretivas de runtime</span><span class="sxs-lookup"><span data-stu-id="fb14b-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="fb14b-106">O arquivo de diretivas de runtime usa o namespace `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="fb14b-107">O elemento raiz é o elemento [Directives](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="fb14b-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="fb14b-108">Ele pode conter zero ou mais elementos [Library](library-element-net-native.md) e zero ou um elemento [Application](application-element-net-native.md), conforme mostrado na estrutura a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb14b-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="fb14b-109">Os atributos do elemento [Application](application-element-net-native.md) podem definir a política de reflexão do runtime de todo o aplicativo ou podem servir como um contêiner para elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="fb14b-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="fb14b-110">O elemento [Library](library-element-net-native.md), por outro lado, é simplesmente um contêiner.</span><span class="sxs-lookup"><span data-stu-id="fb14b-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="fb14b-111">Os filhos dos elementos [Application](application-element-net-native.md) e [Library](library-element-net-native.md) definem os tipos, métodos, campos, propriedades e eventos que estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="fb14b-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="fb14b-112">Para obter informações de referência, escolha os elementos na estrutura de seguir ou consulte [Elementos da diretiva de runtime](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="fb14b-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="fb14b-113">Na seguinte hierarquia, as reticências marcam uma estrutura recursiva.</span><span class="sxs-lookup"><span data-stu-id="fb14b-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="fb14b-114">As informações entre colchetes indicam se o elemento é necessário ou opcional e, se usado, quantas instâncias (uma ou várias) são permitidas.</span><span class="sxs-lookup"><span data-stu-id="fb14b-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

- <span data-ttu-id="fb14b-115">[Directives](directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-115">[Directives](directives-element-net-native.md) [1:1]</span></span>
  - <span data-ttu-id="fb14b-116">[Application](application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-116">[Application](application-element-net-native.md) [0:1]</span></span>
    - <span data-ttu-id="fb14b-117">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-117">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-118">[Namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-118">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-119">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-119">.</span></span> <span data-ttu-id="fb14b-120">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-120">.</span></span>
      - <span data-ttu-id="fb14b-121">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-121">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-122">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-122">.</span></span> <span data-ttu-id="fb14b-123">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-123">.</span></span>
      - <span data-ttu-id="fb14b-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-124">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-125">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-125">.</span></span> <span data-ttu-id="fb14b-126">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-126">.</span></span>
    - <span data-ttu-id="fb14b-127">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-127">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-128">[Namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-128">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-129">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-129">.</span></span> <span data-ttu-id="fb14b-130">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-130">.</span></span>
      - <span data-ttu-id="fb14b-131">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-131">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-132">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-132">.</span></span> <span data-ttu-id="fb14b-133">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-133">.</span></span>
      - <span data-ttu-id="fb14b-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-134">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-135">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-135">.</span></span> <span data-ttu-id="fb14b-136">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-136">.</span></span>
    - <span data-ttu-id="fb14b-137">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-137">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-138">[Subtypes](subtypes-element-net-native.md) (subclasses do tipo recipiente) [O:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-138">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="fb14b-139">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-139">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-140">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-140">.</span></span> <span data-ttu-id="fb14b-141">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-141">.</span></span>
      - <span data-ttu-id="fb14b-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-143">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-143">.</span></span> <span data-ttu-id="fb14b-144">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-144">.</span></span>
      - <span data-ttu-id="fb14b-145">[AttributeImplies](attributeimplies-element-net-native.md) (o tipo recipiente é um atributo) [O:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-145">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="fb14b-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-146">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-147">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-147">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-148">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-148">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-149">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-150">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-151">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="fb14b-152">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-152">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-153">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-153">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-154">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-154">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="fb14b-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-155">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="fb14b-156">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-156">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-157">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-157">.</span></span> <span data-ttu-id="fb14b-158">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-158">.</span></span>
      - <span data-ttu-id="fb14b-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-159">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-160">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-160">.</span></span> <span data-ttu-id="fb14b-161">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-161">.</span></span>
      - <span data-ttu-id="fb14b-162">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-162">[Method](method-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-163">[Parameter](parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-163">[Parameter](parameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-164">[TypeParameter](typeparameter-element-net-native.md) [0:M]</span></span>
        - <span data-ttu-id="fb14b-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-165">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-166">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="fb14b-167">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-167">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-168">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-168">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-169">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-169">[Event](event-element-net-native.md) [0:M]</span></span>
  - <span data-ttu-id="fb14b-170">[Library](library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-170">[Library](library-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="fb14b-171">[Assembly](assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-171">[Assembly](assembly-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-172">[Namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-172">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-173">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-173">.</span></span> <span data-ttu-id="fb14b-174">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-174">.</span></span>
      - <span data-ttu-id="fb14b-175">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-175">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-176">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-176">.</span></span> <span data-ttu-id="fb14b-177">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-177">.</span></span>
      - <span data-ttu-id="fb14b-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-178">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-179">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-179">.</span></span> <span data-ttu-id="fb14b-180">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-180">.</span></span>
    - <span data-ttu-id="fb14b-181">[Namespace](namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-181">[Namespace](namespace-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-182">[Namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-182">[Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-183">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-183">.</span></span> <span data-ttu-id="fb14b-184">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-184">.</span></span>
      - <span data-ttu-id="fb14b-185">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-185">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-186">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-186">.</span></span> <span data-ttu-id="fb14b-187">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-187">.</span></span>
      - <span data-ttu-id="fb14b-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-188">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-189">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-189">.</span></span> <span data-ttu-id="fb14b-190">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-190">.</span></span>
    - <span data-ttu-id="fb14b-191">[Type](type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-191">[Type](type-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-192">[Subtypes](subtypes-element-net-native.md) (subclasses do tipo recipiente) [O:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-192">[Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>
      - <span data-ttu-id="fb14b-193">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-193">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-194">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-194">.</span></span> <span data-ttu-id="fb14b-195">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-195">.</span></span>
      - <span data-ttu-id="fb14b-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-196">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-197">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-197">.</span></span> <span data-ttu-id="fb14b-198">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-198">.</span></span>
      - <span data-ttu-id="fb14b-199">[AttributeImplies](attributeimplies-element-net-native.md) (o tipo recipiente é um atributo) [O:1]</span><span class="sxs-lookup"><span data-stu-id="fb14b-199">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>
      - <span data-ttu-id="fb14b-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-200">[GenericParameter](genericparameter-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-201">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-201">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-202">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="fb14b-203">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-203">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-204">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-204">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-205">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-205">[Event](event-element-net-native.md) [0:M]</span></span>
    - <span data-ttu-id="fb14b-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-206">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>
      - <span data-ttu-id="fb14b-207">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-207">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="fb14b-208">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-208">.</span></span> <span data-ttu-id="fb14b-209">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-209">.</span></span>
      - <span data-ttu-id="fb14b-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="fb14b-210">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="fb14b-211">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-211">.</span></span> <span data-ttu-id="fb14b-212">.</span><span class="sxs-lookup"><span data-stu-id="fb14b-212">.</span></span>
      - <span data-ttu-id="fb14b-213">[Method](method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-213">[Method](method-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-214">[MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>
      - <span data-ttu-id="fb14b-215">[Property](property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-215">[Property](property-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-216">[Field](field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-216">[Field](field-element-net-native.md) [0:M]</span></span>
      - <span data-ttu-id="fb14b-217">[Event](event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="fb14b-217">[Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="fb14b-218">O elemento [Application](application-element-net-native.md) pode não ter nenhum atributo ou pode ter os atributos de política discutidos na [seção de Política e diretiva de runtime](#Directives).</span><span class="sxs-lookup"><span data-stu-id="fb14b-218">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="fb14b-219">Um elemento [Library](library-element-net-native.md) tem um único atributo, `Name`, que especifica o nome de uma biblioteca ou um assembly, sem a extensão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="fb14b-219">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="fb14b-220">Por exemplo, o elemento [Library](library-element-net-native.md) a seguir aplica-se a um assembly denominado Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="fb14b-220">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="fb14b-221">Política e diretivas de runtime</span><span class="sxs-lookup"><span data-stu-id="fb14b-221">Runtime directives and policy</span></span>

<span data-ttu-id="fb14b-222">O próprio elemento [Application](application-element-net-native.md) e os elementos filhos dos elementos [Library](library-element-net-native.md) e [Application](application-element-net-native.md) expressam a política, ou seja, definem a maneira pela qual o aplicativo pode aplicar reflexão a um elemento do programa.</span><span class="sxs-lookup"><span data-stu-id="fb14b-222">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="fb14b-223">O tipo de política é definido por um atributo do elemento (por exemplo, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="fb14b-223">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="fb14b-224">O valor de política é definido pelo valor do atributo (por exemplo, `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="fb14b-224">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="fb14b-225">Qualquer política especificada por um atributo de um elemento aplica-se a todos os elementos filhos que não especifique um valor para essa política.</span><span class="sxs-lookup"><span data-stu-id="fb14b-225">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="fb14b-226">Por exemplo, se uma política é especificada por um elemento [Type](type-element-net-native.md), a política aplica-se a todos os tipos e membros contidos para os quais uma política não foi especificada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-226">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="fb14b-227">A política que pode ser expressa pelos elementos [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) e [Type](type-element-net-native.md) diferem daquela que pode ser expressa para membros individuais (pelos elementos [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md) e [Event](event-element-net-native.md)).</span><span class="sxs-lookup"><span data-stu-id="fb14b-227">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="fb14b-228">Especificando a política para assemblies, namespaces e tipos</span><span class="sxs-lookup"><span data-stu-id="fb14b-228">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="fb14b-229">Os elementos [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) e [Type](type-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-229">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="fb14b-230">`Activate`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-230">`Activate`.</span></span> <span data-ttu-id="fb14b-231">Controla o acesso de runtime a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="fb14b-231">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="fb14b-232">`Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-232">`Browse`.</span></span> <span data-ttu-id="fb14b-233">Controla as consultas para obter informações sobre elementos do programa, mas não permite qualquer acesso do runtime.</span><span class="sxs-lookup"><span data-stu-id="fb14b-233">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="fb14b-234">`Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-234">`Dynamic`.</span></span> <span data-ttu-id="fb14b-235">Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="fb14b-235">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="fb14b-236">`Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-236">`Serialize`.</span></span> <span data-ttu-id="fb14b-237">Controla o acesso ao runtime para construtores, campos e propriedades para habilitar a serialização por bibliotecas de terceiros como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="fb14b-237">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="fb14b-238">`DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-238">`DataContractSerializer`.</span></span> <span data-ttu-id="fb14b-239">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb14b-239">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="fb14b-240">`DataContractJsonSerializer`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-240">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="fb14b-241">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb14b-241">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="fb14b-242">`XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-242">`XmlSerializer`.</span></span> <span data-ttu-id="fb14b-243">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb14b-243">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="fb14b-244">`MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-244">`MarshalObject`.</span></span> <span data-ttu-id="fb14b-245">Controla a política de marshaling de tipos de referência do WinRT e COM.</span><span class="sxs-lookup"><span data-stu-id="fb14b-245">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="fb14b-246">`MarshalDelegate`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-246">`MarshalDelegate`.</span></span> <span data-ttu-id="fb14b-247">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="fb14b-247">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="fb14b-248">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="fb14b-248">`MarshalStructure` .</span></span> <span data-ttu-id="fb14b-249">Controla a política de estruturas de marshaling para código nativo.</span><span class="sxs-lookup"><span data-stu-id="fb14b-249">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="fb14b-250">As configurações associadas a esses tipos de política são:</span><span class="sxs-lookup"><span data-stu-id="fb14b-250">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="fb14b-251">`All`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-251">`All`.</span></span> <span data-ttu-id="fb14b-252">Habilite a política para todos os tipos e membros que a cadeia de ferramentas não remover.</span><span class="sxs-lookup"><span data-stu-id="fb14b-252">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="fb14b-253">`Auto`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-253">`Auto`.</span></span> <span data-ttu-id="fb14b-254">Use o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="fb14b-254">Use the default behavior.</span></span> <span data-ttu-id="fb14b-255">(Não especificar uma política é equivalente à configurar a política para `Auto`, a menos que essa política seja substituída, por exemplo, por um elemento pai.)</span><span class="sxs-lookup"><span data-stu-id="fb14b-255">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="fb14b-256">`Excluded`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-256">`Excluded`.</span></span> <span data-ttu-id="fb14b-257">Desabilite a política para o elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="fb14b-257">Disable the policy for the program element.</span></span>

- <span data-ttu-id="fb14b-258">`Public`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-258">`Public`.</span></span> <span data-ttu-id="fb14b-259">Habilite a política para tipos públicos ou membros, a menos que a cadeia de ferramentas determine que o membro é desnecessário e, portanto, remove-o.</span><span class="sxs-lookup"><span data-stu-id="fb14b-259">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="fb14b-260">(No segundo caso, você deve usar `Required Public` para garantir que o membro é mantido e tem recursos de reflexão.)</span><span class="sxs-lookup"><span data-stu-id="fb14b-260">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="fb14b-261">`PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-261">`PublicAndInternal`.</span></span> <span data-ttu-id="fb14b-262">Habilite a política para tipos ou membros internos e públicos se a cadeia de ferramenta não removê-los.</span><span class="sxs-lookup"><span data-stu-id="fb14b-262">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="fb14b-263">`Required Public`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-263">`Required Public`.</span></span> <span data-ttu-id="fb14b-264">Necessita da cadeia de ferramentas para manter os tipos e membros públicos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="fb14b-264">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="fb14b-265">`Required PublicAndInternal`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-265">`Required PublicAndInternal`.</span></span> <span data-ttu-id="fb14b-266">Necessita da cadeia de ferramentas para manter os tipos e membros públicos e internos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="fb14b-266">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="fb14b-267">`Required All`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-267">`Required All`.</span></span> <span data-ttu-id="fb14b-268">Necessita da cadeia de ferramentas para manter todos os tipos e membros públicos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="fb14b-268">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="fb14b-269">Por exemplo, o seguinte arquivo de diretivas de runtime define a política para todos os tipos e membros no assembly DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="fb14b-269">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="fb14b-270">Ele habilita a reflexão para serialização de todas as propriedades públicas, permite procurar todos os tipos e membros de tipo, permite a ativação de todos os tipos de (devido ao atributo `Dynamic`) e permite a reflexão para todos os tipos e membros públicos.</span><span class="sxs-lookup"><span data-stu-id="fb14b-270">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a><span data-ttu-id="fb14b-271">Especificando a política para membros</span><span class="sxs-lookup"><span data-stu-id="fb14b-271">Specifying policy for members</span></span>

<span data-ttu-id="fb14b-272">Os elementos [Property](property-element-net-native.md) e [Field](field-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-272">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="fb14b-273">`Browse` - Controla as consultas para obter informações este membro, mas não permite qualquer acesso do runtime.</span><span class="sxs-lookup"><span data-stu-id="fb14b-273">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="fb14b-274">`Dynamic` - Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="fb14b-274">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="fb14b-275">Também controla a consulta para obter informações sobre o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-275">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="fb14b-276">`Serialize` - Controla o acesso de runtime ao membro para habilitar as instâncias do tipo a serem serializadas e desserializadas por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="fb14b-276">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="fb14b-277">Esta política pode ser aplicada a construtores, campos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="fb14b-277">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="fb14b-278">Os elementos [Method](method-element-net-native.md) e [Event](event-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-278">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="fb14b-279">`Browse` - Controla as consultas para obter informações este membro, mas não permite qualquer acesso do runtime.</span><span class="sxs-lookup"><span data-stu-id="fb14b-279">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="fb14b-280">`Dynamic` - Controla o acesso a todos os tipos de membro ao runtime, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="fb14b-280">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="fb14b-281">Também controla a consulta para obter informações sobre o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-281">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="fb14b-282">As configurações associadas a esses tipos de política são:</span><span class="sxs-lookup"><span data-stu-id="fb14b-282">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="fb14b-283">`Auto` - Use o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="fb14b-283">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="fb14b-284">(Não especificar uma política é equivalente a configurar essa política como `Auto`, a menos que algo substitua-a.)</span><span class="sxs-lookup"><span data-stu-id="fb14b-284">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="fb14b-285">`Excluded` - Nunca inclua metadados para o membro.</span><span class="sxs-lookup"><span data-stu-id="fb14b-285">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="fb14b-286">`Included` - Habilite a política se o tipo pai estiver presente na saída.</span><span class="sxs-lookup"><span data-stu-id="fb14b-286">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="fb14b-287">`Required` - Necessita que a cadeia de ferramentas mantenha esse membro mesmo se parece ser não usados e habilita a política para ele.</span><span class="sxs-lookup"><span data-stu-id="fb14b-287">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="fb14b-288">Semântica do arquivo de diretivas de runtime</span><span class="sxs-lookup"><span data-stu-id="fb14b-288">Runtime directives file semantics</span></span>

<span data-ttu-id="fb14b-289">A política pode ser definida simultaneamente para elementos de nível superior e de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="fb14b-289">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="fb14b-290">Por exemplo, a política pode ser definida para um assembly e para alguns dos tipos contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="fb14b-290">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="fb14b-291">Se um determinado elemento de nível inferior não for representado, ele herdará a política do pai.</span><span class="sxs-lookup"><span data-stu-id="fb14b-291">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="fb14b-292">Por exemplo, se um elemento `Assembly` estiver presente, mas elementos `Type` não estiverem, a política especificada no elemento `Assembly` se aplica a cada tipo no assembly.</span><span class="sxs-lookup"><span data-stu-id="fb14b-292">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="fb14b-293">Vários elementos também podem aplicar a política ao mesmo elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="fb14b-293">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="fb14b-294">Por exemplo, diferentes elementos [Assembly](assembly-element-net-native.md) podem definir o mesmo elemento de política para o mesmo assembly diferentemente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-294">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="fb14b-295">As seções a seguir explicam como a política para um determinado tipo é resolvida nesses casos.</span><span class="sxs-lookup"><span data-stu-id="fb14b-295">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="fb14b-296">Um elemento [Type](type-element-net-native.md) ou [Method](method-element-net-native.md) de um tipo ou método genérico aplica sua política a todas as instanciações que não têm sua própria política.</span><span class="sxs-lookup"><span data-stu-id="fb14b-296">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="fb14b-297">Por exemplo, um elemento `Type` que especifica a política para <xref:System.Collections.Generic.List%601> aplica-se a todas as instâncias construídas desse tipo genérico, a menos que seja substituído por um determinado tipo genérico construído (como um `List<Int32>`) por um elemento `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-297">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="fb14b-298">Caso contrário, os elementos definem a política para o elemento de programa denominado.</span><span class="sxs-lookup"><span data-stu-id="fb14b-298">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="fb14b-299">Quando um elemento é ambíguo, o mecanismo procura correspondências e, se encontrar uma correspondência exata, ele a usará.</span><span class="sxs-lookup"><span data-stu-id="fb14b-299">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="fb14b-300">Se ele encontrar várias correspondências, haverá um erro ou aviso.</span><span class="sxs-lookup"><span data-stu-id="fb14b-300">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="fb14b-301">Se as duas diretivas aplicam a política ao mesmo elemento de programa</span><span class="sxs-lookup"><span data-stu-id="fb14b-301">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="fb14b-302">Se dois elementos em arquivos de diretivas de runtime diferentes tentarem definir o mesmo tipo de política para o mesmo elemento de programa (como um assembly ou tipo) com valores diferentes, o conflito é resolvido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fb14b-302">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="fb14b-303">Se o elemento `Excluded` estiver presente, ele tem precedência.</span><span class="sxs-lookup"><span data-stu-id="fb14b-303">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="fb14b-304">`Required` tem precedência sobre não `Required`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-304">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="fb14b-305">`All` tem precedência sobre `PublicAndInternal`, que tem precedência sobre `Public`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-305">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="fb14b-306">Qualquer configuração explícita tem precedência sobre `Auto`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-306">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="fb14b-307">Por exemplo, se um único projeto inclui os dois seguintes arquivos de diretivas de runtime, a política de serialização para DataClasses.dll é definida para `Required Public` e `All`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-307">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="fb14b-308">Nesse caso, a política de serialização seria resolvida como `Required All`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-308">In this case, the serialization policy would be resolved as `Required All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

<span data-ttu-id="fb14b-309">No entanto, se duas diretivas em um mesmo arquivo de diretivas de runtime tentarem definir o mesmo tipo de política para o mesmo elemento de programa, a ferramenta de Definição de Esquema de XML exibe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="fb14b-309">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="fb14b-310">Se os elementos filho e pai aplicam o mesmo tipo de política</span><span class="sxs-lookup"><span data-stu-id="fb14b-310">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="fb14b-311">Elementos filhos substituem seus elementos pai, incluindo a configuração `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-311">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="fb14b-312">A substituição é o principal motivo pelo qual você desejaria especificar `Auto`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-312">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="fb14b-313">No exemplo a seguir, a configuração da política de serialização para tudo no `DataClasses` não presente em `DataClasses.ViewModels` seria `Required Public`, e tudo que está presente em ambos `DataClasses` e `DataClasses.ViewModels` seria `All`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-313">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="fb14b-314">Se elementos abertos genéricos e instanciados aplicarem o mesmo tipo de política</span><span class="sxs-lookup"><span data-stu-id="fb14b-314">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="fb14b-315">No exemplo a seguir, `Dictionary<int,int>` recebe a política `Browse` somente se o mecanismo tiver outro motivo para conferir a política `Browse` (que seria o comportamento padrão); todas as outras instanciações do <xref:System.Collections.Generic.Dictionary%602> terão todos os seus membros pesquisáveis.</span><span class="sxs-lookup"><span data-stu-id="fb14b-315">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a><span data-ttu-id="fb14b-316">Como a política é deduzida</span><span class="sxs-lookup"><span data-stu-id="fb14b-316">How policy is inferred</span></span>

<span data-ttu-id="fb14b-317">Cada tipo de política possui um conjunto de regras diferente que determina como a presença desse tipo de política afeta outros constructos.</span><span class="sxs-lookup"><span data-stu-id="fb14b-317">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="fb14b-318">O efeito da política Browse</span><span class="sxs-lookup"><span data-stu-id="fb14b-318">The effect of Browse policy</span></span>

<span data-ttu-id="fb14b-319">Aplicar a política `Browse` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-319">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-320">O tipo base do tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-320">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-321">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-322">Se o tipo for um delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-322">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-323">Cada interface do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-323">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-324">O tipo de cada atributo aplicado ao tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-324">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-325">Se o tipo for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-325">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-326">Se o tipo for genérico, os tipos pelos quais o tipo é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-326">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="fb14b-327">Aplicar a política `Browse` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-327">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-328">Cada tipo de parâmetro do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-328">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-329">O tipo de retorno do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-329">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-330">O tipo recipiente do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-330">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-331">Se o método for um método genérico instanciado, o método genérico não instanciado é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-331">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-332">O tipo de cada atributo aplicado ao método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-332">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-333">Se o método for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-333">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-334">Se o método for genérico, os tipos pelos quais o método é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-334">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="fb14b-335">Aplicar a política `Browse` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-335">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-336">O tipo de cada atributo aplicado ao campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-336">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-337">O tipo do campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-337">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-338">O tipo ao qual o campo pertence é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-338">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="fb14b-339">O efeito da política Dynamic</span><span class="sxs-lookup"><span data-stu-id="fb14b-339">The effect of Dynamic policy</span></span>

<span data-ttu-id="fb14b-340">Aplicar a política `Dynamic` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-340">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-341">O tipo base do tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-341">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-342">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-342">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-343">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-343">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-344">Cada interface do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-344">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-345">O tipo de cada atributo aplicado ao tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-345">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-346">Se o tipo for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-346">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-347">Se o tipo for genérico, os tipos pelos quais o tipo é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-347">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="fb14b-348">Aplicar a política `Dynamic` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-348">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-349">Cada tipo de parâmetro do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-349">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-350">O tipo de retorno do método é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-350">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-351">O tipo recipiente do método é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-351">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-352">Se o método for um método genérico instanciado, o método genérico não instanciado é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-352">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-353">O tipo de cada atributo aplicado ao método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-353">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-354">Se o método for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-354">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-355">Se o método for genérico, os tipos pelos quais o método é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-355">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-356">O método pode ser invocado por `MethodInfo.Invoke`, e a criação de delegado é possibilitada por <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb14b-356">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="fb14b-357">Aplicar a política `Dynamic` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-357">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-358">O tipo de cada atributo aplicado ao campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-358">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-359">O tipo do campo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-359">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-360">O tipo ao qual o campo pertence é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-360">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="fb14b-361">O efeito da política Activation</span><span class="sxs-lookup"><span data-stu-id="fb14b-361">The effect of Activation policy</span></span>

<span data-ttu-id="fb14b-362">Aplicar a política de Ativação a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-362">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-363">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-363">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-364">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-364">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-365">Construtores de tipo são marcados com a política `Activation`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-365">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="fb14b-366">Aplicar a política `Activation` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-366">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="fb14b-367">O construtor pode ser invocado pelos métodos <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> e <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb14b-367">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="fb14b-368">Para métodos, a política `Activation` afeta apenas construtores.</span><span class="sxs-lookup"><span data-stu-id="fb14b-368">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="fb14b-369">Aplicar a política `Activation` a um campo não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="fb14b-369">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="fb14b-370">O efeito da política Serialize</span><span class="sxs-lookup"><span data-stu-id="fb14b-370">The effect of Serialize policy</span></span>

<span data-ttu-id="fb14b-371">A política `Serialize` permite o uso de serializadores comuns baseados em reflexão.</span><span class="sxs-lookup"><span data-stu-id="fb14b-371">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="fb14b-372">No entanto, como os padrões de acesso de reflexão exata de serializadores não Microsoft não são conhecidos pela Microsoft, essa política pode não ser totalmente eficiente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-372">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="fb14b-373">Aplicar a política `Serialize` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-373">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-374">O tipo base do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-374">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-375">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-375">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="fb14b-376">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-376">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="fb14b-377">Se o tipo é uma enumeração, uma matriz do tipo é marcada com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-377">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-378">Se o tipo implementa <xref:System.Collections.Generic.IEnumerable%601>, `T` é marcada com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-378">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-379">Se o tipo for <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601> ou <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` e <xref:System.Collections.Generic.List%601> são marcados com a política `Serialize`, mas nenhum membro do tipo de interface é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-379">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-380">Se o tipo for <xref:System.Collections.Generic.List%601>, nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-380">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-381">Se o tipo for <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-381">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="fb14b-382">mas nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-382">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-383">Se o tipo for <xref:System.Collections.Generic.Dictionary%602>, nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-383">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-384">Se o tipo implementa <xref:System.Collections.Generic.IDictionary%602>, `TKey` e `TValue` são marcados com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-384">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-385">Cada construtor, cada acesso de propriedade e cada campo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-385">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="fb14b-386">Aplicar a política `Serialize` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-386">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-387">O tipo recipiente estiver marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-387">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-388">O tipo de retorno do método é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-388">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="fb14b-389">Aplicar a política `Serialize` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="fb14b-389">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="fb14b-390">O tipo recipiente estiver marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-390">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="fb14b-391">O tipo do campo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="fb14b-391">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="fb14b-392">O efeito das políticas XmlSerializer, DataContractSerializer e DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="fb14b-392">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="fb14b-393">Ao contrário da `Serialize` política, que é destinada a serializadores baseados em reflexão, as <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> políticas, e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> são usadas para habilitar um conjunto de serializadores que são conhecidos para a cadeia de ferramentas de .net Native.</span><span class="sxs-lookup"><span data-stu-id="fb14b-393">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="fb14b-394">Esses serializadores não são implementados usando reflexão, mas o conjunto de tipos que pode ser serializado no tempo de execução é determinado de maneira semelhante, como tipos reflexíveis.</span><span class="sxs-lookup"><span data-stu-id="fb14b-394">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="fb14b-395">Aplicar de uma dessas políticas a um tipo permite que o tipo seja serializado com o serializador correspondente.</span><span class="sxs-lookup"><span data-stu-id="fb14b-395">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="fb14b-396">Além disso, quaisquer tipos que o mecanismo de serialização determinar estaticamente como necessitando serialização também serão serializáveis.</span><span class="sxs-lookup"><span data-stu-id="fb14b-396">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="fb14b-397">Essas políticas não têm efeito nos campos ou métodos.</span><span class="sxs-lookup"><span data-stu-id="fb14b-397">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="fb14b-398">Para obter mais informações, consulte a seção "Diferenças em serializadores" em [Migrar seu aplicativo da Windows Store para .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="fb14b-398">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb14b-399">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb14b-399">See also</span></span>

- [<span data-ttu-id="fb14b-400">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="fb14b-400">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="fb14b-401">Reflexão e .NET Nativo</span><span class="sxs-lookup"><span data-stu-id="fb14b-401">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
