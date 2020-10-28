---
title: Definir atributos do assembly
description: Você pode definir atributos de assembly para um assembly .NET, incluindo identidade de assembly, informativo, manifesto de assembly e atributos de nome forte.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 32318d647dee8f3f397e3497e7c2da640bd492d0
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687674"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="04d87-103">Definir atributos do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-103">Set assembly attributes</span></span>

<span data-ttu-id="04d87-104">Os atributos de assembly são valores que fornecem informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-104">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="04d87-105">Os atributos são divididos nos seguintes conjuntos de informações:</span><span class="sxs-lookup"><span data-stu-id="04d87-105">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="04d87-106">Atributos de identidade do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-106">Assembly identity attributes</span></span>

- <span data-ttu-id="04d87-107">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="04d87-107">Informational attributes</span></span>

- <span data-ttu-id="04d87-108">Atributos de manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-108">Assembly manifest attributes</span></span>

- <span data-ttu-id="04d87-109">Atributos de nome forte</span><span class="sxs-lookup"><span data-stu-id="04d87-109">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="04d87-110">Atributos de identidade do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-110">Assembly identity attributes</span></span>

<span data-ttu-id="04d87-111">Três atributos, com um nome forte (se aplicável), determinam a identidade de um assembly: nome, versão e cultura.</span><span class="sxs-lookup"><span data-stu-id="04d87-111">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="04d87-112">Esses atributos formam o nome completo do assembly e são necessários ao fazer referência ao assembly no código.</span><span class="sxs-lookup"><span data-stu-id="04d87-112">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="04d87-113">Você pode usar atributos para definir a versão e a cultura de um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-113">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="04d87-114">O compilador ou o [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) define o valor do nome quando o assembly é criado, com base no arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-114">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="04d87-115">A tabela a seguir descreve os atributos de versão e cultura.</span><span class="sxs-lookup"><span data-stu-id="04d87-115">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="04d87-116">Atributo de identidade do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-116">Assembly identity attribute</span></span>|<span data-ttu-id="04d87-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d87-117">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="04d87-118">Campo enumerado que indica a cultura compatível com o assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-118">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="04d87-119">Um assembly também pode especificar a independência da cultura, indicando que ela contém os recursos para a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="04d87-119">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="04d87-120">**Observação:** o runtime trata qualquer assembly que não tenha o atributo de cultura definido como nulo, como um assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="04d87-120">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="04d87-121">Esses assemblies estão sujeitos às regras de associação de assembly satélite.</span><span class="sxs-lookup"><span data-stu-id="04d87-121">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="04d87-122">Para obter mais informações, consulte [como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="04d87-122">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="04d87-123">O valor que define os atributos de assembly; por exemplo, se o assembly pode ser executado lado a lado.</span><span class="sxs-lookup"><span data-stu-id="04d87-123">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="04d87-124">Valor numérico no formato *principal* . *secundário* . *compilação* . *revisão* (por exemplo, 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="04d87-124">Numeric value in the format *major* . *minor* . *build* . *revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="04d87-125">O Common Language Runtime usa esse valor para executar operações de associação em assemblies com nome forte.</span><span class="sxs-lookup"><span data-stu-id="04d87-125">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="04d87-126">**Observação:**  Se o <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributo não for aplicado a um assembly, o número de versão especificado pelo <xref:System.Reflection.AssemblyVersionAttribute> atributo será usado pelas <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> Propriedades, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04d87-126">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="04d87-127">O exemplo de código a seguir mostra como aplicar os atributos de versão e cultura a um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-127">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="04d87-128">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="04d87-128">Informational attributes</span></span>

<span data-ttu-id="04d87-129">Você pode usar atributos informativos para fornecer informações adicionais corporativas ou de produto para um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-129">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="04d87-130">A tabela a seguir descreve os atributos informativos que você pode aplicar a um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-130">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="04d87-131">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="04d87-131">Informational attribute</span></span>|<span data-ttu-id="04d87-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d87-132">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="04d87-133">O valor de cadeia de caracteres que especifica um nome de empresa.</span><span class="sxs-lookup"><span data-stu-id="04d87-133">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="04d87-134">O valor de cadeia de caracteres que especifica informações sobre direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="04d87-134">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="04d87-135">O valor de cadeia de caracteres que especifica o número de versão do arquivo Win32.</span><span class="sxs-lookup"><span data-stu-id="04d87-135">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="04d87-136">Isso normalmente tem como padrão a versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-136">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="04d87-137">O valor de cadeia de caracteres que especifica informações de versão que não são usadas pelo Common Language Runtime, como o número de versão completo de um produto.</span><span class="sxs-lookup"><span data-stu-id="04d87-137">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="04d87-138">**Observação:** se esse atributo for aplicado a um assembly, a cadeia de caracteres que ele especifica poderá ser obtida no tempo de execução usando a propriedade <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04d87-138">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="04d87-139">A cadeia de caracteres também é usada na chave do Registro e no caminho fornecidos pelas propriedades <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04d87-139">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="04d87-140">O valor de cadeia de caracteres que especifica informações do produto.</span><span class="sxs-lookup"><span data-stu-id="04d87-140">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="04d87-141">O valor de cadeia de caracteres que especifica informações de marca registrada.</span><span class="sxs-lookup"><span data-stu-id="04d87-141">String value specifying trademark information.</span></span>|

<span data-ttu-id="04d87-142">Esses atributos podem aparecer na página Propriedades do Windows do assembly ou podem ser substituídos usando a opção de compilador **/win32res** para especificar seu próprio arquivo de recurso Win32.</span><span class="sxs-lookup"><span data-stu-id="04d87-142">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="04d87-143">Atributos de manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-143">Assembly manifest attributes</span></span>

<span data-ttu-id="04d87-144">Também é possível usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly, incluindo título, descrição, o alias padrão e a configuração.</span><span class="sxs-lookup"><span data-stu-id="04d87-144">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="04d87-145">A tabela a seguir descreve os atributos de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-145">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="04d87-146">Atributo de manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="04d87-146">Assembly manifest attribute</span></span>|<span data-ttu-id="04d87-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d87-147">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="04d87-148">O valor de cadeia de caracteres que indica a configuração do assembly, como Retail ou Depuração.</span><span class="sxs-lookup"><span data-stu-id="04d87-148">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="04d87-149">O runtime não usa esse valor.</span><span class="sxs-lookup"><span data-stu-id="04d87-149">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="04d87-150">O valor de cadeia de caracteres que especifica um alias padrão a ser usado ao fazer referências de assemblies.</span><span class="sxs-lookup"><span data-stu-id="04d87-150">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="04d87-151">Esse valor fornece um nome amigável quando o nome do assembly em si não o for (como um valor GUID).</span><span class="sxs-lookup"><span data-stu-id="04d87-151">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="04d87-152">Esse valor também pode ser usado como uma forma abreviada do nome completo do assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-152">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="04d87-153">O valor de cadeia de caracteres que especifica uma breve descrição que resume a natureza e o objetivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-153">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="04d87-154">O valor de cadeia de caracteres que especifica um nome amigável para o assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-154">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="04d87-155">Por exemplo, um assembly chamado *comdlg* pode ter o título controle de caixa de diálogo comum da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="04d87-155">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="04d87-156">Atributos de nome forte</span><span class="sxs-lookup"><span data-stu-id="04d87-156">Strong name attributes</span></span>

<span data-ttu-id="04d87-157">Você pode usar atributos de nome forte para definir um nome forte para um assembly.</span><span class="sxs-lookup"><span data-stu-id="04d87-157">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="04d87-158">A tabela a seguir descreve os atributos de nome forte.</span><span class="sxs-lookup"><span data-stu-id="04d87-158">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="04d87-159">Atributo de nome forte</span><span class="sxs-lookup"><span data-stu-id="04d87-159">Strong name attribute</span></span>|<span data-ttu-id="04d87-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="04d87-160">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="04d87-161">O valor booliano que indica que a assinatura em atraso está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="04d87-161">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="04d87-162">O valor de cadeia de caracteres que indica o nome do arquivo que contém a chave pública (se usando assinatura em atraso) ou as chaves pública e privada passadas como um parâmetro ao construtor desse atributo.</span><span class="sxs-lookup"><span data-stu-id="04d87-162">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="04d87-163">Observe que o nome do arquivo é relativo ao caminho do arquivo de saída (o *. exe* ou *. dll* ), não o caminho do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="04d87-163">Note that the file name is relative to the output file path (the *.exe* or *.dll* ), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="04d87-164">Indica o contêiner de chaves que contém o par de chaves passado como um parâmetro ao construtor desse atributo.</span><span class="sxs-lookup"><span data-stu-id="04d87-164">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="04d87-165">O exemplo de código a seguir mostra os atributos a serem aplicados ao usar a assinatura de atraso para criar um assembly de nome forte com um arquivo de chave pública chamado *myKey. SNK* .</span><span class="sxs-lookup"><span data-stu-id="04d87-165">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk* .</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="04d87-166">Veja também</span><span class="sxs-lookup"><span data-stu-id="04d87-166">See also</span></span>

- [<span data-ttu-id="04d87-167">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="04d87-167">Create assemblies</span></span>](create.md)
