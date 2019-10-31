---
title: Referência do arquivo de configuração de diretivas do tempo de execução (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: f4c51dc269775d14d395cb464b3787cc987e086d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128136"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="bd720-102">Referência do arquivo de configuração de diretivas do tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="bd720-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>

<span data-ttu-id="bd720-103">O arquivo de diretivas de tempo de execução (. rd.xml) é um arquivo de configuração XML que especifica se os elementos do programa designado estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="bd720-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="bd720-104">Aqui está um exemplo de um arquivo de diretivas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="bd720-104">Here’s an example of a runtime directives file:</span></span>

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

## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="bd720-105">A estrutura de um arquivo de diretivas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bd720-105">The structure of a runtime directives file</span></span>

<span data-ttu-id="bd720-106">O arquivo de diretivas de tempo de execução usa o namespace `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span><span class="sxs-lookup"><span data-stu-id="bd720-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>

<span data-ttu-id="bd720-107">O elemento raiz é o elemento [Directives](directives-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="bd720-107">The root element is the [Directives](directives-element-net-native.md) element.</span></span> <span data-ttu-id="bd720-108">Ele pode conter zero ou mais elementos [Library](library-element-net-native.md) e zero ou um elemento [Application](application-element-net-native.md), conforme mostrado na estrutura a seguir.</span><span class="sxs-lookup"><span data-stu-id="bd720-108">It can contain zero or more [Library](library-element-net-native.md) elements, and zero or one [Application](application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="bd720-109">Os atributos do elemento [Application](application-element-net-native.md) podem definir a política de reflexão do tempo de execução de todo o aplicativo ou podem servir como um contêiner para elementos filhos.</span><span class="sxs-lookup"><span data-stu-id="bd720-109">The attributes of the [Application](application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="bd720-110">O elemento [Library](library-element-net-native.md), por outro lado, é simplesmente um contêiner.</span><span class="sxs-lookup"><span data-stu-id="bd720-110">The [Library](library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="bd720-111">Os filhos dos elementos [Application](application-element-net-native.md) e [Library](library-element-net-native.md) definem os tipos, métodos, campos, propriedades e eventos que estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="bd720-111">The children of the [Application](application-element-net-native.md) and [Library](library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>

<span data-ttu-id="bd720-112">Para obter informações de referência, escolha os elementos na estrutura de seguir ou consulte [Elementos da diretiva de tempo de execução](runtime-directive-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bd720-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](runtime-directive-elements.md).</span></span> <span data-ttu-id="bd720-113">Na seguinte hierarquia, as reticências marcam uma estrutura recursiva.</span><span class="sxs-lookup"><span data-stu-id="bd720-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="bd720-114">As informações entre colchetes indicam se o elemento é necessário ou opcional e, se usado, quantas instâncias (uma ou várias) são permitidas.</span><span class="sxs-lookup"><span data-stu-id="bd720-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>

<span data-ttu-id="bd720-115">[Diretivas](directives-element-net-native.md) [1:1] [aplicativo](application-element-net-native.md) [0:1] [assembly](assembly-element-net-native.md) [0: M] [namespace](namespace-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="bd720-115">[Directives](directives-element-net-native.md) [1:1] [Application](application-element-net-native.md) [0:1] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-116">.</span><span class="sxs-lookup"><span data-stu-id="bd720-116">.</span></span> <span data-ttu-id="bd720-117">.</span><span class="sxs-lookup"><span data-stu-id="bd720-117">.</span></span>
<span data-ttu-id="bd720-118">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-118">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-119">.</span><span class="sxs-lookup"><span data-stu-id="bd720-119">.</span></span> <span data-ttu-id="bd720-120">.</span><span class="sxs-lookup"><span data-stu-id="bd720-120">.</span></span>
<span data-ttu-id="bd720-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-121">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-122">.</span><span class="sxs-lookup"><span data-stu-id="bd720-122">.</span></span> <span data-ttu-id="bd720-123">.</span><span class="sxs-lookup"><span data-stu-id="bd720-123">.</span></span>
<span data-ttu-id="bd720-124">[Namespace [0](namespace-element-net-native.md) : m] [namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-124">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-125">.</span><span class="sxs-lookup"><span data-stu-id="bd720-125">.</span></span> <span data-ttu-id="bd720-126">.</span><span class="sxs-lookup"><span data-stu-id="bd720-126">.</span></span>
<span data-ttu-id="bd720-127">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-127">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-128">.</span><span class="sxs-lookup"><span data-stu-id="bd720-128">.</span></span> <span data-ttu-id="bd720-129">.</span><span class="sxs-lookup"><span data-stu-id="bd720-129">.</span></span>
<span data-ttu-id="bd720-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-130">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-131">.</span><span class="sxs-lookup"><span data-stu-id="bd720-131">.</span></span> <span data-ttu-id="bd720-132">.</span><span class="sxs-lookup"><span data-stu-id="bd720-132">.</span></span>
<span data-ttu-id="bd720-133">[Digite](type-element-net-native.md) [0: M] [subtipos](subtypes-element-net-native.md) (subclasses do tipo recipiente) [O:1] [tipo](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-133">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-134">.</span><span class="sxs-lookup"><span data-stu-id="bd720-134">.</span></span> <span data-ttu-id="bd720-135">.</span><span class="sxs-lookup"><span data-stu-id="bd720-135">.</span></span>
<span data-ttu-id="bd720-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-136">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-137">.</span><span class="sxs-lookup"><span data-stu-id="bd720-137">.</span></span> <span data-ttu-id="bd720-138">.</span><span class="sxs-lookup"><span data-stu-id="bd720-138">.</span></span>
<span data-ttu-id="bd720-139">[AttributeImplies](attributeimplies-element-net-native.md) (tipo recipiente é um atributo) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: m] [método](method-element-net-native.md) [0: M] [parâmetro](parameter-element-net-native.md) [0: m] [TypeParameter](typeparameter-element-net-native.md) [0: m] [GenericParameter](genericparameter-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) ( método genérico construído) [0: M] [Propriedade](property-element-net-native.md) [0: m] [campo](field-element-net-native.md) [0: m] [evento](event-element-net-native.md) [0: m] [TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: m] [tipo](type-element-net-native.md) [0: m].</span><span class="sxs-lookup"><span data-stu-id="bd720-139">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-140">.</span><span class="sxs-lookup"><span data-stu-id="bd720-140">.</span></span> <span data-ttu-id="bd720-141">.</span><span class="sxs-lookup"><span data-stu-id="bd720-141">.</span></span>
<span data-ttu-id="bd720-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-142">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-143">.</span><span class="sxs-lookup"><span data-stu-id="bd720-143">.</span></span> <span data-ttu-id="bd720-144">.</span><span class="sxs-lookup"><span data-stu-id="bd720-144">.</span></span>
<span data-ttu-id="bd720-145">[Método](method-element-net-native.md) [0: m] [parâmetro](parameter-element-net-native.md) [0: m] [TypeParameter](typeparameter-element-net-native.md) [0: M] [GenericParameter](genericparameter-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0: m] [Propriedade](property-element-net-native.md) [0: M] [campo](field-element-net-native.md) [0: m] [evento](event-element-net-native.md) [0: m] [ Biblioteca](library-element-net-native.md) [0: m] [assembly](assembly-element-net-native.md) [0: m] [namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-145">[Method](method-element-net-native.md) [0:M] [Parameter](parameter-element-net-native.md) [0:M] [TypeParameter](typeparameter-element-net-native.md) [0:M] [GenericParameter](genericparameter-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [Library](library-element-net-native.md) [0:M] [Assembly](assembly-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-146">.</span><span class="sxs-lookup"><span data-stu-id="bd720-146">.</span></span> <span data-ttu-id="bd720-147">.</span><span class="sxs-lookup"><span data-stu-id="bd720-147">.</span></span>
<span data-ttu-id="bd720-148">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-148">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-149">.</span><span class="sxs-lookup"><span data-stu-id="bd720-149">.</span></span> <span data-ttu-id="bd720-150">.</span><span class="sxs-lookup"><span data-stu-id="bd720-150">.</span></span>
<span data-ttu-id="bd720-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-151">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-152">.</span><span class="sxs-lookup"><span data-stu-id="bd720-152">.</span></span> <span data-ttu-id="bd720-153">.</span><span class="sxs-lookup"><span data-stu-id="bd720-153">.</span></span>
<span data-ttu-id="bd720-154">[Namespace [0](namespace-element-net-native.md) : m] [namespace](namespace-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-154">[Namespace](namespace-element-net-native.md) [0:M] [Namespace](namespace-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-155">.</span><span class="sxs-lookup"><span data-stu-id="bd720-155">.</span></span> <span data-ttu-id="bd720-156">.</span><span class="sxs-lookup"><span data-stu-id="bd720-156">.</span></span>
<span data-ttu-id="bd720-157">[Digite](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-157">[Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-158">.</span><span class="sxs-lookup"><span data-stu-id="bd720-158">.</span></span> <span data-ttu-id="bd720-159">.</span><span class="sxs-lookup"><span data-stu-id="bd720-159">.</span></span>
<span data-ttu-id="bd720-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-160">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-161">.</span><span class="sxs-lookup"><span data-stu-id="bd720-161">.</span></span> <span data-ttu-id="bd720-162">.</span><span class="sxs-lookup"><span data-stu-id="bd720-162">.</span></span>
<span data-ttu-id="bd720-163">[Digite](type-element-net-native.md) [0: M] [subtipos](subtypes-element-net-native.md) (subclasses do tipo recipiente) [O:1] [tipo](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-163">[Type](type-element-net-native.md) [0:M] [Subtypes](subtypes-element-net-native.md) (subclasses of the containing type) [O:1] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-164">.</span><span class="sxs-lookup"><span data-stu-id="bd720-164">.</span></span> <span data-ttu-id="bd720-165">.</span><span class="sxs-lookup"><span data-stu-id="bd720-165">.</span></span>
<span data-ttu-id="bd720-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-166">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-167">.</span><span class="sxs-lookup"><span data-stu-id="bd720-167">.</span></span> <span data-ttu-id="bd720-168">.</span><span class="sxs-lookup"><span data-stu-id="bd720-168">.</span></span>
<span data-ttu-id="bd720-169">[AttributeImplies](attributeimplies-element-net-native.md) (tipo recipiente é um atributo) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0: m] [método](method-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0: m] [Propriedade](property-element-net-native.md) [0: m] [campo](field-element-net-native.md) [0: m] [evento](event-element-net-native.md) [0 : M] [TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: m] [tipo](type-element-net-native.md) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-169">[AttributeImplies](attributeimplies-element-net-native.md) (containing type is an attribute) [O:1] [GenericParameter](genericparameter-element-net-native.md) [0:M] [Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M] [TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] [Type](type-element-net-native.md) [0:M] .</span></span> <span data-ttu-id="bd720-170">.</span><span class="sxs-lookup"><span data-stu-id="bd720-170">.</span></span> <span data-ttu-id="bd720-171">.</span><span class="sxs-lookup"><span data-stu-id="bd720-171">.</span></span>
<span data-ttu-id="bd720-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (tipo genérico construído) [0: M].</span><span class="sxs-lookup"><span data-stu-id="bd720-172">[TypeInstantiation](typeinstantiation-element-net-native.md) (constructed generic type) [0:M] .</span></span> <span data-ttu-id="bd720-173">.</span><span class="sxs-lookup"><span data-stu-id="bd720-173">.</span></span> <span data-ttu-id="bd720-174">.</span><span class="sxs-lookup"><span data-stu-id="bd720-174">.</span></span>
<span data-ttu-id="bd720-175">[Método](method-element-net-native.md) [0: m] [MethodInstantiation](methodinstantiation-element-net-native.md) (método genérico construído) [0: m] [Propriedade](property-element-net-native.md) [0: M] [campo](field-element-net-native.md) [0: m] [evento](event-element-net-native.md) [0: m]</span><span class="sxs-lookup"><span data-stu-id="bd720-175">[Method](method-element-net-native.md) [0:M] [MethodInstantiation](methodinstantiation-element-net-native.md) (constructed generic method) [0:M] [Property](property-element-net-native.md) [0:M] [Field](field-element-net-native.md) [0:M] [Event](event-element-net-native.md) [0:M]</span></span>

<span data-ttu-id="bd720-176">O elemento [Application](application-element-net-native.md) pode não ter nenhum atributo ou pode ter os atributos de política discutidos na [seção de Política e diretiva de tempo de execução](#Directives).</span><span class="sxs-lookup"><span data-stu-id="bd720-176">The [Application](application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>

<span data-ttu-id="bd720-177">Um elemento [Library](library-element-net-native.md) tem um único atributo, `Name`, que especifica o nome de uma biblioteca ou um assembly, sem a extensão do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bd720-177">A [Library](library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="bd720-178">Por exemplo, o elemento [Library](library-element-net-native.md) a seguir aplica-se a um assembly denominado Extensions.dll.</span><span class="sxs-lookup"><span data-stu-id="bd720-178">For example, the following [Library](library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>

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

## <a name="runtime-directives-and-policy"></a><span data-ttu-id="bd720-179">Política e diretivas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bd720-179">Runtime directives and policy</span></span>

<span data-ttu-id="bd720-180">O próprio elemento [Application](application-element-net-native.md) e os elementos filhos dos elementos [Library](library-element-net-native.md) e [Application](application-element-net-native.md) expressam a política, ou seja, definem a maneira pela qual o aplicativo pode aplicar reflexão a um elemento do programa.</span><span class="sxs-lookup"><span data-stu-id="bd720-180">The [Application](application-element-net-native.md) element itself and the child elements of the [Library](library-element-net-native.md) and [Application](application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="bd720-181">O tipo de política é definido por um atributo do elemento (por exemplo, `Serialize`).</span><span class="sxs-lookup"><span data-stu-id="bd720-181">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="bd720-182">O valor de política é definido pelo valor do atributo (por exemplo, `Serialize="Required"`).</span><span class="sxs-lookup"><span data-stu-id="bd720-182">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>

<span data-ttu-id="bd720-183">Qualquer política especificada por um atributo de um elemento aplica-se a todos os elementos filhos que não especifique um valor para essa política.</span><span class="sxs-lookup"><span data-stu-id="bd720-183">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="bd720-184">Por exemplo, se uma política é especificada por um elemento [Type](type-element-net-native.md), a política aplica-se a todos os tipos e membros contidos para os quais uma política não foi especificada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="bd720-184">For example, if a policy is specified by a [Type](type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>

<span data-ttu-id="bd720-185">A política que pode ser expressa pelos elementos [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) e [Type](type-element-net-native.md) diferem daquela que pode ser expressa para membros individuais (pelos elementos [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md) e [Event](event-element-net-native.md)).</span><span class="sxs-lookup"><span data-stu-id="bd720-185">The policy that can be expressed by the [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](method-element-net-native.md), [Property](property-element-net-native.md), [Field](field-element-net-native.md), and [Event](event-element-net-native.md) elements).</span></span>

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="bd720-186">Especificando a política para assemblies, namespaces e tipos</span><span class="sxs-lookup"><span data-stu-id="bd720-186">Specifying policy for assemblies, namespaces, and types</span></span>

<span data-ttu-id="bd720-187">Os elementos [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md) e [Type](type-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-187">The [Application](application-element-net-native.md), [Assembly](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [Namespace](namespace-element-net-native.md), [Subtypes](subtypes-element-net-native.md), and [Type](type-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="bd720-188">`Activate`</span><span class="sxs-lookup"><span data-stu-id="bd720-188">`Activate`.</span></span> <span data-ttu-id="bd720-189">Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.</span><span class="sxs-lookup"><span data-stu-id="bd720-189">Controls runtime access to constructors, to enable activation of instances.</span></span>

- <span data-ttu-id="bd720-190">`Browse`</span><span class="sxs-lookup"><span data-stu-id="bd720-190">`Browse`.</span></span> <span data-ttu-id="bd720-191">Controla as consultas para obter informações sobre elementos do programa, mas não permite qualquer acesso do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd720-191">Controls querying for information about program elements but does not enable any runtime access.</span></span>

- <span data-ttu-id="bd720-192">`Dynamic`</span><span class="sxs-lookup"><span data-stu-id="bd720-192">`Dynamic`.</span></span> <span data-ttu-id="bd720-193">Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="bd720-193">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>

- <span data-ttu-id="bd720-194">`Serialize`</span><span class="sxs-lookup"><span data-stu-id="bd720-194">`Serialize`.</span></span> <span data-ttu-id="bd720-195">Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização por bibliotecas de terceiros como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="bd720-195">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>

- <span data-ttu-id="bd720-196">`DataContractSerializer`</span><span class="sxs-lookup"><span data-stu-id="bd720-196">`DataContractSerializer`.</span></span> <span data-ttu-id="bd720-197">Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd720-197">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="bd720-198">`DataContractJsonSerializer`</span><span class="sxs-lookup"><span data-stu-id="bd720-198">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="bd720-199">Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd720-199">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="bd720-200">`XmlSerializer`</span><span class="sxs-lookup"><span data-stu-id="bd720-200">`XmlSerializer`.</span></span> <span data-ttu-id="bd720-201">Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd720-201">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>

- <span data-ttu-id="bd720-202">`MarshalObject`</span><span class="sxs-lookup"><span data-stu-id="bd720-202">`MarshalObject`.</span></span> <span data-ttu-id="bd720-203">Controla a política de marshaling de tipos de referência do WinRT e COM.</span><span class="sxs-lookup"><span data-stu-id="bd720-203">Controls policy for marshaling reference types to WinRT and COM.</span></span>

- <span data-ttu-id="bd720-204">`MarshalDelegate`</span><span class="sxs-lookup"><span data-stu-id="bd720-204">`MarshalDelegate`.</span></span> <span data-ttu-id="bd720-205">Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.</span><span class="sxs-lookup"><span data-stu-id="bd720-205">Controls policy for marshaling delegate types as function pointers to native code.</span></span>

- <span data-ttu-id="bd720-206">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="bd720-206">`MarshalStructure` .</span></span> <span data-ttu-id="bd720-207">Controla a política de estruturas de marshaling para código nativo.</span><span class="sxs-lookup"><span data-stu-id="bd720-207">Controls policy for marshaling structures to native code.</span></span>

<span data-ttu-id="bd720-208">As configurações associadas a esses tipos de política são:</span><span class="sxs-lookup"><span data-stu-id="bd720-208">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="bd720-209">`All`</span><span class="sxs-lookup"><span data-stu-id="bd720-209">`All`.</span></span> <span data-ttu-id="bd720-210">Habilite a política para todos os tipos e membros que a cadeia de ferramentas não remover.</span><span class="sxs-lookup"><span data-stu-id="bd720-210">Enable the policy for all types and members that the tool chain does not remove.</span></span>

- <span data-ttu-id="bd720-211">`Auto`</span><span class="sxs-lookup"><span data-stu-id="bd720-211">`Auto`.</span></span> <span data-ttu-id="bd720-212">Use o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="bd720-212">Use the default behavior.</span></span> <span data-ttu-id="bd720-213">(Não especificar uma política é equivalente à configurar a política para `Auto`, a menos que essa política seja substituída, por exemplo, por um elemento pai.)</span><span class="sxs-lookup"><span data-stu-id="bd720-213">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>

- <span data-ttu-id="bd720-214">`Excluded`</span><span class="sxs-lookup"><span data-stu-id="bd720-214">`Excluded`.</span></span> <span data-ttu-id="bd720-215">Desabilite a política para o elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="bd720-215">Disable the policy for the program element.</span></span>

- <span data-ttu-id="bd720-216">`Public`</span><span class="sxs-lookup"><span data-stu-id="bd720-216">`Public`.</span></span> <span data-ttu-id="bd720-217">Habilite a política para tipos públicos ou membros, a menos que a cadeia de ferramentas determine que o membro é desnecessário e, portanto, remove-o.</span><span class="sxs-lookup"><span data-stu-id="bd720-217">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="bd720-218">(No segundo caso, você deve usar `Required Public` para garantir que o membro é mantido e tem recursos de reflexão.)</span><span class="sxs-lookup"><span data-stu-id="bd720-218">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>

- <span data-ttu-id="bd720-219">`PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="bd720-219">`PublicAndInternal`.</span></span> <span data-ttu-id="bd720-220">Habilite a política para tipos ou membros internos e públicos se a cadeia de ferramenta não removê-los.</span><span class="sxs-lookup"><span data-stu-id="bd720-220">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>

- <span data-ttu-id="bd720-221">`Required Public`</span><span class="sxs-lookup"><span data-stu-id="bd720-221">`Required Public`.</span></span> <span data-ttu-id="bd720-222">Necessita da cadeia de ferramentas para manter os tipos e membros públicos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="bd720-222">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="bd720-223">`Required PublicAndInternal`</span><span class="sxs-lookup"><span data-stu-id="bd720-223">`Required PublicAndInternal`.</span></span> <span data-ttu-id="bd720-224">Necessita da cadeia de ferramentas para manter os tipos e membros públicos e internos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="bd720-224">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>

- <span data-ttu-id="bd720-225">`Required All`</span><span class="sxs-lookup"><span data-stu-id="bd720-225">`Required All`.</span></span> <span data-ttu-id="bd720-226">Necessita da cadeia de ferramentas para manter todos os tipos e membros públicos, sejam usados ou não, e habilita a política para eles.</span><span class="sxs-lookup"><span data-stu-id="bd720-226">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>

<span data-ttu-id="bd720-227">Por exemplo, o seguinte arquivo de diretivas de tempo de execução define a política para todos os tipos e membros no assembly DataClasses.dll.</span><span class="sxs-lookup"><span data-stu-id="bd720-227">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="bd720-228">Ele habilita a reflexão para serialização de todas as propriedades públicas, permite procurar todos os tipos e membros de tipo, permite a ativação de todos os tipos de (devido ao atributo `Dynamic`) e permite a reflexão para todos os tipos e membros públicos.</span><span class="sxs-lookup"><span data-stu-id="bd720-228">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>

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

### <a name="specifying-policy-for-members"></a><span data-ttu-id="bd720-229">Especificando a política para membros</span><span class="sxs-lookup"><span data-stu-id="bd720-229">Specifying policy for members</span></span>

<span data-ttu-id="bd720-230">Os elementos [Property](property-element-net-native.md) e [Field](field-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-230">The [Property](property-element-net-native.md) and [Field](field-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="bd720-231">`Browse` - Controla as consultas para obter informações este membro, mas não permite qualquer acesso do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd720-231">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>

- <span data-ttu-id="bd720-232">`Dynamic` - Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="bd720-232">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="bd720-233">Também controla a consulta para obter informações sobre o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="bd720-233">Also controls querying for information about the containing type.</span></span>

- <span data-ttu-id="bd720-234">`Serialize` - Controla o acesso de tempo de execução ao membro para habilitar as instâncias do tipo a serem serializadas e desserializadas por bibliotecas como o serializador Newtonsoft JSON.</span><span class="sxs-lookup"><span data-stu-id="bd720-234">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="bd720-235">Esta política pode ser aplicada a construtores, campos e propriedades.</span><span class="sxs-lookup"><span data-stu-id="bd720-235">This policy can be applied to constructors, fields, and properties.</span></span>

<span data-ttu-id="bd720-236">Os elementos [Method](method-element-net-native.md) e [Event](event-element-net-native.md) dão suporte aos seguintes tipos de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-236">The [Method](method-element-net-native.md) and [Event](event-element-net-native.md) elements support the following policy types:</span></span>

- <span data-ttu-id="bd720-237">`Browse` - Controla as consultas para obter informações este membro, mas não permite qualquer acesso do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bd720-237">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>

- <span data-ttu-id="bd720-238">`Dynamic` - Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.</span><span class="sxs-lookup"><span data-stu-id="bd720-238">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="bd720-239">Também controla a consulta para obter informações sobre o tipo recipiente.</span><span class="sxs-lookup"><span data-stu-id="bd720-239">Also controls querying for information about the containing type.</span></span>

 <span data-ttu-id="bd720-240">As configurações associadas a esses tipos de política são:</span><span class="sxs-lookup"><span data-stu-id="bd720-240">The settings associated with these policy types are:</span></span>

- <span data-ttu-id="bd720-241">`Auto` - Use o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="bd720-241">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="bd720-242">(Não especificar uma política é equivalente a configurar essa política como `Auto`, a menos que algo substitua-a.)</span><span class="sxs-lookup"><span data-stu-id="bd720-242">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>

- <span data-ttu-id="bd720-243">`Excluded` - Nunca inclua metadados para o membro.</span><span class="sxs-lookup"><span data-stu-id="bd720-243">`Excluded` - Never include metadata for the member.</span></span>

- <span data-ttu-id="bd720-244">`Included` - Habilite a política se o tipo pai estiver presente na saída.</span><span class="sxs-lookup"><span data-stu-id="bd720-244">`Included` - Enable the policy if the parent type is present in the output.</span></span>

- <span data-ttu-id="bd720-245">`Required` - Necessita que a cadeia de ferramentas mantenha esse membro mesmo se parece ser não usados e habilita a política para ele.</span><span class="sxs-lookup"><span data-stu-id="bd720-245">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>

## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="bd720-246">Semântica do arquivo de diretivas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bd720-246">Runtime directives file semantics</span></span>

<span data-ttu-id="bd720-247">A política pode ser definida simultaneamente para elementos de nível superior e de nível inferior.</span><span class="sxs-lookup"><span data-stu-id="bd720-247">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="bd720-248">Por exemplo, a política pode ser definida para um assembly e para alguns dos tipos contidos neste assembly.</span><span class="sxs-lookup"><span data-stu-id="bd720-248">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="bd720-249">Se um determinado elemento de nível inferior não for representado, ele herdará a política do pai.</span><span class="sxs-lookup"><span data-stu-id="bd720-249">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="bd720-250">Por exemplo, se um elemento `Assembly` estiver presente, mas elementos `Type` não estiverem, a política especificada no elemento `Assembly` se aplica a cada tipo no assembly.</span><span class="sxs-lookup"><span data-stu-id="bd720-250">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="bd720-251">Vários elementos também podem aplicar a política ao mesmo elemento de programa.</span><span class="sxs-lookup"><span data-stu-id="bd720-251">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="bd720-252">Por exemplo, diferentes elementos [Assembly](assembly-element-net-native.md) podem definir o mesmo elemento de política para o mesmo assembly diferentemente.</span><span class="sxs-lookup"><span data-stu-id="bd720-252">For example, separate [Assembly](assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="bd720-253">As seções a seguir explicam como a política para um determinado tipo é resolvida nesses casos.</span><span class="sxs-lookup"><span data-stu-id="bd720-253">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>

<span data-ttu-id="bd720-254">Um elemento [Type](type-element-net-native.md) ou [Method](method-element-net-native.md) de um tipo ou método genérico aplica sua política a todas as instanciações que não têm sua própria política.</span><span class="sxs-lookup"><span data-stu-id="bd720-254">A [Type](type-element-net-native.md) or [Method](method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="bd720-255">Por exemplo, um elemento `Type` que especifica a política para <xref:System.Collections.Generic.List%601> aplica-se a todas as instâncias construídas desse tipo genérico, a menos que seja substituído por um determinado tipo genérico construído (como um `List<Int32>`) por um elemento `TypeInstantiation`.</span><span class="sxs-lookup"><span data-stu-id="bd720-255">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="bd720-256">Caso contrário, os elementos definem a política para o elemento de programa denominado.</span><span class="sxs-lookup"><span data-stu-id="bd720-256">Otherwise, elements define policy for the program element named.</span></span>

<span data-ttu-id="bd720-257">Quando um elemento é ambíguo, o mecanismo procura correspondências e, se encontrar uma correspondência exata, ele a usará.</span><span class="sxs-lookup"><span data-stu-id="bd720-257">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="bd720-258">Se ele encontrar várias correspondências, haverá um erro ou aviso.</span><span class="sxs-lookup"><span data-stu-id="bd720-258">If it finds multiple matches, there will be a warning or error.</span></span>

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="bd720-259">Se as duas diretivas aplicam a política ao mesmo elemento de programa</span><span class="sxs-lookup"><span data-stu-id="bd720-259">If two directives apply policy to the same program element</span></span>

<span data-ttu-id="bd720-260">Se dois elementos em arquivos de diretivas de tempo de execução diferentes tentarem definir o mesmo tipo de política para o mesmo elemento de programa (como um assembly ou tipo) com valores diferentes, o conflito é resolvido da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bd720-260">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>

1. <span data-ttu-id="bd720-261">Se o elemento `Excluded` estiver presente, ele tem precedência.</span><span class="sxs-lookup"><span data-stu-id="bd720-261">If the `Excluded` element is present, it has precedence.</span></span>

2. <span data-ttu-id="bd720-262">`Required` tem precedência sobre não `Required`.</span><span class="sxs-lookup"><span data-stu-id="bd720-262">`Required` has precedence over not `Required`.</span></span>

3. <span data-ttu-id="bd720-263">`All` tem precedência sobre `PublicAndInternal`, que tem precedência sobre `Public`.</span><span class="sxs-lookup"><span data-stu-id="bd720-263">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>

4. <span data-ttu-id="bd720-264">Qualquer configuração explícita tem precedência sobre `Auto`.</span><span class="sxs-lookup"><span data-stu-id="bd720-264">Any explicit setting has precedence over `Auto`.</span></span>

<span data-ttu-id="bd720-265">Por exemplo, se um único projeto inclui os dois seguintes arquivos de diretivas de tempo de execução, a política de serialização para DataClasses.dll é definida para `Required Public` e `All`.</span><span class="sxs-lookup"><span data-stu-id="bd720-265">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="bd720-266">Nesse caso, a política de serialização seria resolvida como `Required All`.</span><span class="sxs-lookup"><span data-stu-id="bd720-266">In this case, the serialization policy would be resolved as `Required All`.</span></span>

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

<span data-ttu-id="bd720-267">No entanto, se duas diretivas em um mesmo arquivo de diretivas de tempo de execução tentarem definir o mesmo tipo de política para o mesmo elemento de programa, a ferramenta de Definição de Esquema de XML exibe uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="bd720-267">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="bd720-268">Se os elementos filho e pai aplicam o mesmo tipo de política</span><span class="sxs-lookup"><span data-stu-id="bd720-268">If child and parent elements apply the same policy type</span></span>

<span data-ttu-id="bd720-269">Elementos filhos substituem seus elementos pai, incluindo a configuração `Excluded`.</span><span class="sxs-lookup"><span data-stu-id="bd720-269">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="bd720-270">A substituição é o principal motivo pelo qual você desejaria especificar `Auto`.</span><span class="sxs-lookup"><span data-stu-id="bd720-270">Overriding is the main reason you would want to specify `Auto`.</span></span>

<span data-ttu-id="bd720-271">No exemplo a seguir, a configuração da política de serialização para tudo no `DataClasses` não presente em `DataClasses.ViewModels` seria `Required Public`, e tudo que está presente em ambos `DataClasses` e `DataClasses.ViewModels` seria `All`.</span><span class="sxs-lookup"><span data-stu-id="bd720-271">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="bd720-272">Se elementos abertos genéricos e instanciados aplicarem o mesmo tipo de política</span><span class="sxs-lookup"><span data-stu-id="bd720-272">If open generics and instantiated elements apply the same policy type</span></span>

<span data-ttu-id="bd720-273">No exemplo a seguir, `Dictionary<int,int>` recebe a política `Browse` somente se o mecanismo tiver outro motivo para conferir a política `Browse` (que seria o comportamento padrão); todas as outras instanciações do <xref:System.Collections.Generic.Dictionary%602> terão todos os seus membros pesquisáveis.</span><span class="sxs-lookup"><span data-stu-id="bd720-273">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>

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

### <a name="how-policy-is-inferred"></a><span data-ttu-id="bd720-274">Como a política é deduzida</span><span class="sxs-lookup"><span data-stu-id="bd720-274">How policy is inferred</span></span>

<span data-ttu-id="bd720-275">Cada tipo de política possui um conjunto de regras diferente que determina como a presença desse tipo de política afeta outros constructos.</span><span class="sxs-lookup"><span data-stu-id="bd720-275">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>

#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="bd720-276">O efeito da política Browse</span><span class="sxs-lookup"><span data-stu-id="bd720-276">The effect of Browse policy</span></span>

<span data-ttu-id="bd720-277">Aplicar a política `Browse` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-277">Applying the `Browse` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-278">O tipo base do tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-278">The base type of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-279">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-279">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-280">Se o tipo for um delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-280">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-281">Cada interface do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-281">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-282">O tipo de cada atributo aplicado ao tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-282">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-283">Se o tipo for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-283">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-284">Se o tipo for genérico, os tipos pelos quais o tipo é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-284">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="bd720-285">Aplicar a política `Browse` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-285">Applying the `Browse` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-286">Cada tipo de parâmetro do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-286">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-287">O tipo de retorno do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-287">The return type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-288">O tipo recipiente do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-288">The containing type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-289">Se o método for um método genérico instanciado, o método genérico não instanciado é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-289">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-290">O tipo de cada atributo aplicado ao método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-290">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-291">Se o método for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-291">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-292">Se o método for genérico, os tipos pelos quais o método é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-292">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="bd720-293">Aplicar a política `Browse` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-293">Applying the `Browse` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-294">O tipo de cada atributo aplicado ao campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-294">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-295">O tipo do campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-295">The type of the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-296">O tipo ao qual o campo pertence é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-296">The type to which the field belongs is marked with the `Browse` policy.</span></span>

#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="bd720-297">O efeito da política Dynamic</span><span class="sxs-lookup"><span data-stu-id="bd720-297">The effect of Dynamic policy</span></span>

<span data-ttu-id="bd720-298">Aplicar a política `Dynamic` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-298">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-299">O tipo base do tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-299">The base type of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-300">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-300">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-301">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-301">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-302">Cada interface do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-302">Each interface of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-303">O tipo de cada atributo aplicado ao tipo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-303">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-304">Se o tipo for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-304">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-305">Se o tipo for genérico, os tipos pelos quais o tipo é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-305">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>

<span data-ttu-id="bd720-306">Aplicar a política `Dynamic` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-306">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-307">Cada tipo de parâmetro do método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-307">Each parameter type of the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-308">O tipo de retorno do método é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-308">The return type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-309">O tipo recipiente do método é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-309">The containing type of the method is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-310">Se o método for um método genérico instanciado, o método genérico não instanciado é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-310">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-311">O tipo de cada atributo aplicado ao método é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-311">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-312">Se o método for genérico, cada tipo de restrição é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-312">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-313">Se o método for genérico, os tipos pelos quais o método é instanciado são marcados com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-313">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-314">O método pode ser invocado por `MethodInfo.Invoke`, e a criação de delegado é possibilitada por <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd720-314">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bd720-315">Aplicar a política `Dynamic` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-315">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-316">O tipo de cada atributo aplicado ao campo é marcado com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-316">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-317">O tipo do campo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-317">The type of the field is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-318">O tipo ao qual o campo pertence é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-318">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>

#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="bd720-319">O efeito da política Activation</span><span class="sxs-lookup"><span data-stu-id="bd720-319">The effect of Activation policy</span></span>

<span data-ttu-id="bd720-320">Aplicar a política de Ativação a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-320">Applying the Activation policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-321">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-321">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-322">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-322">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-323">Construtores de tipo são marcados com a política `Activation`.</span><span class="sxs-lookup"><span data-stu-id="bd720-323">Constructors of the type are marked with the `Activation` policy.</span></span>

<span data-ttu-id="bd720-324">Aplicar a política `Activation` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-324">Applying the `Activation` policy to a method involves the following policy change:</span></span>

- <span data-ttu-id="bd720-325">O construtor pode ser invocado pelos métodos <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> e <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd720-325">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bd720-326">Para métodos, a política `Activation` afeta apenas construtores.</span><span class="sxs-lookup"><span data-stu-id="bd720-326">For methods, the `Activation` policy affects constructors only.</span></span>

<span data-ttu-id="bd720-327">Aplicar a política `Activation` a um campo não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="bd720-327">Applying the `Activation` policy to a field has no effect.</span></span>

#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="bd720-328">O efeito da política Serialize</span><span class="sxs-lookup"><span data-stu-id="bd720-328">The effect of Serialize policy</span></span>

<span data-ttu-id="bd720-329">A política `Serialize` permite o uso de serializadores comuns baseados em reflexão.</span><span class="sxs-lookup"><span data-stu-id="bd720-329">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="bd720-330">No entanto, como os padrões de acesso de reflexão exata de serializadores não Microsoft não são conhecidos pela Microsoft, essa política pode não ser totalmente eficiente.</span><span class="sxs-lookup"><span data-stu-id="bd720-330">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>

<span data-ttu-id="bd720-331">Aplicar a política `Serialize` a um tipo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-331">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-332">O tipo base do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-332">The base type of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-333">Se o tipo for um tipo genérico instanciado, a versão não instanciada do tipo é marcada com a política `Browse`.</span><span class="sxs-lookup"><span data-stu-id="bd720-333">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>

- <span data-ttu-id="bd720-334">Se o tipo for um tipo delegado, o método `Invoke` no tipo é marcado com a política `Dynamic`.</span><span class="sxs-lookup"><span data-stu-id="bd720-334">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>

- <span data-ttu-id="bd720-335">Se o tipo é uma enumeração, uma matriz do tipo é marcada com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-335">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-336">Se o tipo implementa <xref:System.Collections.Generic.IEnumerable%601>, `T` é marcada com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-336">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-337">Se o tipo for <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601> ou <xref:System.Collections.Generic.IReadOnlyList%601>, `T[]` e <xref:System.Collections.Generic.List%601> são marcados com a política `Serialize`, mas nenhum membro do tipo de interface é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-337">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-338">Se o tipo for <xref:System.Collections.Generic.List%601>, nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-338">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-339">Se o tipo for <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-339">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="bd720-340">mas nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-340">but no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-341">Se o tipo for <xref:System.Collections.Generic.Dictionary%602>, nenhum membro do tipo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-341">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-342">Se o tipo implementa <xref:System.Collections.Generic.IDictionary%602>, `TKey` e `TValue` são marcados com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-342">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-343">Cada construtor, cada acesso de propriedade e cada campo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-343">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="bd720-344">Aplicar a política `Serialize` a um método envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-344">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-345">O tipo recipiente estiver marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-345">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-346">O tipo de retorno do método é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-346">The return type of the method is marked with the `Serialize` policy.</span></span>

<span data-ttu-id="bd720-347">Aplicar a política `Serialize` a um campo envolve as seguintes alterações de política:</span><span class="sxs-lookup"><span data-stu-id="bd720-347">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>

- <span data-ttu-id="bd720-348">O tipo recipiente estiver marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-348">The containing type is marked with the `Serialize` policy.</span></span>

- <span data-ttu-id="bd720-349">O tipo do campo é marcado com a política `Serialize`.</span><span class="sxs-lookup"><span data-stu-id="bd720-349">The type of the field is marked with the `Serialize` policy.</span></span>

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a><span data-ttu-id="bd720-350">O efeito das políticas XmlSerializer, DataContractSerializer e DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="bd720-350">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerializer policies</span></span>

<span data-ttu-id="bd720-351">Ao contrário da política de `Serialize`, que é destinada a serializadores baseados em reflexão, as políticas <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> são usadas para habilitar um conjunto de serializadores que são conhecidos pela cadeia de ferramentas .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bd720-351">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> policies are used to enable a set of serializers that are known to the .NET Native tool chain.</span></span> <span data-ttu-id="bd720-352">Esses serializadores não são implementados usando reflexão, mas o conjunto de tipos que pode ser serializado no tempo de execução é determinado de maneira semelhante, como tipos reflexíveis.</span><span class="sxs-lookup"><span data-stu-id="bd720-352">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>

<span data-ttu-id="bd720-353">Aplicar de uma dessas políticas a um tipo permite que o tipo seja serializado com o serializador correspondente.</span><span class="sxs-lookup"><span data-stu-id="bd720-353">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="bd720-354">Além disso, quaisquer tipos que o mecanismo de serialização determinar estaticamente como necessitando serialização também serão serializáveis.</span><span class="sxs-lookup"><span data-stu-id="bd720-354">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>

<span data-ttu-id="bd720-355">Essas políticas não têm efeito nos campos ou métodos.</span><span class="sxs-lookup"><span data-stu-id="bd720-355">These policies have no effect on methods or fields.</span></span>

<span data-ttu-id="bd720-356">Para obter mais informações, consulte a seção "Diferenças em serializadores" em [Migrar seu aplicativo da Windows Store para .NET Native](migrating-your-windows-store-app-to-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="bd720-356">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](migrating-your-windows-store-app-to-net-native.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd720-357">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd720-357">See also</span></span>

- [<span data-ttu-id="bd720-358">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bd720-358">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="bd720-359">Reflexão e .NET Native</span><span class="sxs-lookup"><span data-stu-id="bd720-359">Reflection and .NET Native</span></span>](reflection-and-net-native.md)
