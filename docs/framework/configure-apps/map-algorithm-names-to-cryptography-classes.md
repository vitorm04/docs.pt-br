---
title: Mapeando nomes de algoritmo para classes de criptografia
description: Mapeie os nomes de algoritmos para classes de criptografia no .NET. Um desenvolvedor tem quatro opções para criar um objeto de criptografia.
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
ms.openlocfilehash: 5a1d7acdd34182dd82f4dce66d136c4ef4de6e95
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105346"
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="6021c-104">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="6021c-104">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="6021c-105">Há quatro maneiras pelas quais um desenvolvedor pode criar um objeto de criptografia usando o SDK do Windows:</span><span class="sxs-lookup"><span data-stu-id="6021c-105">There are four ways a developer can create a cryptography object using the Windows SDK:</span></span>  
  
- <span data-ttu-id="6021c-106">Crie um objeto usando o operador **New** .</span><span class="sxs-lookup"><span data-stu-id="6021c-106">Create an object by using the **new** operator.</span></span>  
  
- <span data-ttu-id="6021c-107">Crie um objeto que implemente um algoritmo de criptografia específico chamando o método **Create** na classe abstrata para esse algoritmo.</span><span class="sxs-lookup"><span data-stu-id="6021c-107">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
- <span data-ttu-id="6021c-108">Crie um objeto que implemente um algoritmo de criptografia específico chamando o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="6021c-108">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="6021c-109">Crie um objeto que implemente uma classe de algoritmos criptográficos (como uma codificação de bloco simétrico) chamando o método **Create** na classe abstrata para esse tipo de algoritmo (como <xref:System.Security.Cryptography.SymmetricAlgorithm> ).</span><span class="sxs-lookup"><span data-stu-id="6021c-109">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="6021c-110">Por exemplo, suponha que um desenvolvedor queira calcular o hash SHA1 de um conjunto de bytes.</span><span class="sxs-lookup"><span data-stu-id="6021c-110">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="6021c-111">O <xref:System.Security.Cryptography> namespace contém duas implementações do algoritmo SHA1, uma implementação puramente gerenciada e outra que encapsula a CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="6021c-111">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="6021c-112">O desenvolvedor pode optar por criar uma instância de uma implementação SHA1 específica (como a <xref:System.Security.Cryptography.SHA1Managed> ) chamando o operador **New** .</span><span class="sxs-lookup"><span data-stu-id="6021c-112">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="6021c-113">No entanto, se não importa qual classe o Common Language Runtime carrega contanto que a classe implemente o algoritmo hash SHA1, o desenvolvedor pode criar um objeto chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="6021c-113">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6021c-114">Esse método chama **System. Security. Cryptography. CryptoConfig. CreateFromName ("System. Security. Cryptography. SHA1")**, que deve retornar uma implementação do algoritmo de hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="6021c-114">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="6021c-115">O desenvolvedor também pode chamar **System. Security. Cryptography. CryptoConfig ("SHA1")** porque, por padrão, a configuração de criptografia inclui nomes curtos para os algoritmos fornecidos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6021c-115">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="6021c-116">Se não importa qual algoritmo de hash é usado, o desenvolvedor pode chamar o <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> método, que retorna um objeto que implementa uma transformação de hash.</span><span class="sxs-lookup"><span data-stu-id="6021c-116">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="6021c-117">Mapeando nomes de algoritmos em arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6021c-117">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="6021c-118">Por padrão, o tempo de execução retorna um <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objeto para todos os quatro cenários.</span><span class="sxs-lookup"><span data-stu-id="6021c-118">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="6021c-119">No entanto, um administrador de máquina pode alterar o tipo de objeto que os métodos nos dois últimos cenários retornam.</span><span class="sxs-lookup"><span data-stu-id="6021c-119">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="6021c-120">Para fazer isso, você deve mapear um nome de algoritmo amigável para a classe que deseja usar no arquivo de configuração de computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6021c-120">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="6021c-121">O exemplo a seguir mostra como configurar o tempo de execução para que **System. Security. Cryptography. SHA1. Create**, **System. Security. CryptoConfig. CreateFromName ("SHA1")** e **System. Security. Cryptography. HashAlgorithm. Create** retorne um `MySHA1HashClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="6021c-121">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
```xml  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 <span data-ttu-id="6021c-122">Você pode especificar o nome do atributo no [ \> elemento<cryptoClass](./file-schema/cryptography/cryptoclass-element.md) (o exemplo anterior nomeia o atributo `MySHA1Hash` ).</span><span class="sxs-lookup"><span data-stu-id="6021c-122">You can specify the name of the attribute in the [<cryptoClass\> element](./file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="6021c-123">O valor do atributo no **\<cryptoClass>** elemento é uma cadeia de caracteres que o Common Language Runtime usa para localizar a classe.</span><span class="sxs-lookup"><span data-stu-id="6021c-123">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="6021c-124">Você pode usar qualquer cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="6021c-124">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="6021c-125">Muitos nomes de algoritmos podem ser mapeados para a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="6021c-125">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="6021c-126">O [ \<nameEntry> elemento](./file-schema/cryptography/nameentry-element.md) mapeia uma classe para um nome de algoritmo amigável.</span><span class="sxs-lookup"><span data-stu-id="6021c-126">The [\<nameEntry> element](./file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="6021c-127">O atributo **Name** pode ser uma cadeia de caracteres que é usada ao chamar o método **System. Security. Cryptography. CryptoConfig. CreateFromName** ou o nome de uma classe de criptografia abstrata no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="6021c-127">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="6021c-128">O valor do atributo **Class** é o nome do atributo no **\<cryptoClass>** elemento.</span><span class="sxs-lookup"><span data-stu-id="6021c-128">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6021c-129">Você pode obter um algoritmo SHA1 chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> ou o método **Security. CryptoConfig. CreateFromName ("SHA1")** .</span><span class="sxs-lookup"><span data-stu-id="6021c-129">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="6021c-130">Cada método garante apenas que ele retorne um objeto que implementa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="6021c-130">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="6021c-131">Você não precisa mapear cada nome amigável de um algoritmo para a mesma classe no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6021c-131">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="6021c-132">Para obter uma lista de nomes padrão e as classes que eles mapeiam, consulte <xref:System.Security.Cryptography.CryptoConfig> .</span><span class="sxs-lookup"><span data-stu-id="6021c-132">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6021c-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="6021c-133">See also</span></span>

- [<span data-ttu-id="6021c-134">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="6021c-134">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6021c-135">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="6021c-135">Configuring Cryptography Classes</span></span>](configure-cryptography-classes.md)
