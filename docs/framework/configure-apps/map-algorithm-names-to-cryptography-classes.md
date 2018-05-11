---
title: Mapeando nomes de algoritmo para classes de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2dc03c3aa6808ed4ce0c22f4e69fa8c98cb7aebd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a><span data-ttu-id="9b875-102">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="9b875-102">Mapping Algorithm Names to Cryptography Classes</span></span>
<span data-ttu-id="9b875-103">Há quatro maneiras que um desenvolvedor pode criar um objeto de criptografia usando o [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="9b875-103">There are four ways a developer can create a cryptography object using the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:</span></span>  
  
-   <span data-ttu-id="9b875-104">Criar um objeto usando o **novo** operador.</span><span class="sxs-lookup"><span data-stu-id="9b875-104">Create an object by using the **new** operator.</span></span>  
  
-   <span data-ttu-id="9b875-105">Criar um objeto que implementa um algoritmo de criptografia determinado chamando o **criar** método na classe abstrata para aquele algoritmo.</span><span class="sxs-lookup"><span data-stu-id="9b875-105">Create an object that implements a particular cryptography algorithm by calling the **Create** method on the abstract class for that algorithm.</span></span>  
  
-   <span data-ttu-id="9b875-106">Criar um objeto que implementa um algoritmo de criptografia determinado chamando o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="9b875-106">Create an object that implements a particular cryptography algorithm by calling the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="9b875-107">Criar um objeto que implementa uma classe de algoritmos criptográficos (como uma codificação de bloco simétrica) ao chamar o **criar** método na classe abstrata para esse tipo de algoritmo (como <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span><span class="sxs-lookup"><span data-stu-id="9b875-107">Create an object that implements a class of cryptographic algorithms (such as a symmetric block cipher) by calling the **Create** method on the abstract class for that type of algorithm (such as <xref:System.Security.Cryptography.SymmetricAlgorithm>).</span></span>  
  
 <span data-ttu-id="9b875-108">Por exemplo, suponha que um desenvolvedor deseja computar o hash SHA1 de um conjunto de bytes.</span><span class="sxs-lookup"><span data-stu-id="9b875-108">For example, suppose a developer wants to compute the SHA1 hash of a set of bytes.</span></span> <span data-ttu-id="9b875-109">O <xref:System.Security.Cryptography> namespace contém duas implementações de algoritmo SHA1, uma implementação totalmente gerenciada e um que encapsula o CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="9b875-109">The <xref:System.Security.Cryptography> namespace contains two implementations of the SHA1 algorithm, one purely managed implementation and one that wraps CryptoAPI.</span></span> <span data-ttu-id="9b875-110">O desenvolvedor pode optar por criar uma instância de uma implementação específica do SHA1 (como o <xref:System.Security.Cryptography.SHA1Managed>) chamando o **novo** operador.</span><span class="sxs-lookup"><span data-stu-id="9b875-110">The developer can choose to instantiate a particular SHA1 implementation (such as the <xref:System.Security.Cryptography.SHA1Managed>) by calling the **new** operator.</span></span> <span data-ttu-id="9b875-111">No entanto, se não importa qual classe o common language runtime carrega desde que a classe implementa o algoritmo de hash SHA1, o desenvolvedor pode criar um objeto chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="9b875-111">However, if it does not matter which class the common language runtime loads as long as the class implements the SHA1 hash algorithm, the developer can create an object by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9b875-112">Este método chama **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, que deve retornar uma implementação do algoritmo de hash SHA1.</span><span class="sxs-lookup"><span data-stu-id="9b875-112">This method calls **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, which must return an implementation of the SHA1 hash algorithm.</span></span>  
  
 <span data-ttu-id="9b875-113">O desenvolvedor também pode chamar **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** porque, por padrão, a configuração de criptografia inclui nomes curtos para os algoritmos fornecidos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b875-113">The developer can also call **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** because, by default, cryptography configuration includes short names for the algorithms shipped in the .NET Framework.</span></span>  
  
 <span data-ttu-id="9b875-114">Se não importa qual algoritmo de hash é usado, o desenvolvedor pode chamar o <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> método, que retorna um objeto que implementa uma transformação de hash.</span><span class="sxs-lookup"><span data-stu-id="9b875-114">If it does not matter which hash algorithm is used, the developer can call the <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> method, which returns an object that implements a hashing transformation.</span></span>  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a><span data-ttu-id="9b875-115">Mapeando nomes de algoritmo em arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9b875-115">Mapping Algorithm Names in Configuration Files</span></span>  
 <span data-ttu-id="9b875-116">Por padrão, o tempo de execução retorna um <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objeto para todos os quatro cenários.</span><span class="sxs-lookup"><span data-stu-id="9b875-116">By default, the runtime returns a <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> object for all four scenarios.</span></span> <span data-ttu-id="9b875-117">No entanto, um administrador do computador pode alterar o tipo de objeto que retornam os métodos nos últimos dois cenários.</span><span class="sxs-lookup"><span data-stu-id="9b875-117">However, a machine administrator can change the type of object that the methods in the last two scenarios return.</span></span> <span data-ttu-id="9b875-118">Para fazer isso, você deve mapear um nome amigável do algoritmo para a classe que você deseja usar no arquivo de configuração da máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9b875-118">To do this, you must map a friendly algorithm name to the class you want to use in the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="9b875-119">O exemplo a seguir mostra como configurar o tempo de execução para que **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, e  **System.Security.Cryptography.HashAlgorithm.Create** retornar um `MySHA1HashClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="9b875-119">The following example shows how to configure the runtime so that **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, and **System.Security.Cryptography.HashAlgorithm.Create** return a `MySHA1HashClass` object.</span></span>  
  
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
  
 <span data-ttu-id="9b875-120">Você pode especificar o nome do atributo no [< cryptoClass\> elemento](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (no exemplo anterior nomeia o atributo `MySHA1Hash`).</span><span class="sxs-lookup"><span data-stu-id="9b875-120">You can specify the name of the attribute in the [<cryptoClass\> element](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (the previous example names the attribute `MySHA1Hash`).</span></span> <span data-ttu-id="9b875-121">O valor do atributo no  **\<cryptoClass >** elemento é uma cadeia de caracteres que o common language runtime usa para localizar a classe.</span><span class="sxs-lookup"><span data-stu-id="9b875-121">The value of the attribute in the **\<cryptoClass>** element is a string that the common language runtime uses to find the class.</span></span> <span data-ttu-id="9b875-122">Você pode usar qualquer cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="9b875-122">You can use any string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>  
  
 <span data-ttu-id="9b875-123">Muitos nomes de algoritmo podem mapear para a mesma classe.</span><span class="sxs-lookup"><span data-stu-id="9b875-123">Many algorithm names can map to the same class.</span></span> <span data-ttu-id="9b875-124">O [ \<nameEntry > elemento](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mapeia uma classe para um nome amigável do algoritmo.</span><span class="sxs-lookup"><span data-stu-id="9b875-124">The [\<nameEntry> element](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) maps a class to one friendly algorithm name.</span></span> <span data-ttu-id="9b875-125">O **nome** atributo pode ser uma cadeia de caracteres que é usada ao chamar o **System.Security.Cryptography.CryptoConfig.CreateFromName** método ou o nome de uma classe abstrata de criptografia no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="9b875-125">The **name** attribute can be either a string that is used when calling the **System.Security.Cryptography.CryptoConfig.CreateFromName** method or the name of an abstract cryptography class in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="9b875-126">O valor de **classe** atributo é o nome do atributo no  **\<cryptoClass >** elemento.</span><span class="sxs-lookup"><span data-stu-id="9b875-126">The value of the **class** attribute is the name of the attribute in the **\<cryptoClass>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b875-127">Você pode obter um algoritmo SHA1 chamando o <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> ou **Security.CryptoConfig.CreateFromName("SHA1")** método.</span><span class="sxs-lookup"><span data-stu-id="9b875-127">You can get an SHA1 algorithm by calling the <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> or the **Security.CryptoConfig.CreateFromName("SHA1")** method.</span></span> <span data-ttu-id="9b875-128">Cada método apenas garante que ela retorna um objeto que implementa o algoritmo SHA1.</span><span class="sxs-lookup"><span data-stu-id="9b875-128">Each method guarantees only that it returns an object that implements the SHA1 algorithm.</span></span> <span data-ttu-id="9b875-129">Você não precisa mapear cada nome amigável de um algoritmo para a mesma classe no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9b875-129">You do not have to map each friendly name of an algorithm to the same class in the configuration file.</span></span>  
  
 <span data-ttu-id="9b875-130">Para obter uma lista de nomes padrão e as classes que são mapeados para, consulte <xref:System.Security.Cryptography.CryptoConfig>.</span><span class="sxs-lookup"><span data-stu-id="9b875-130">For a list of default names and the classes they map to, see <xref:System.Security.Cryptography.CryptoConfig>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b875-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b875-131">See Also</span></span>  
 [<span data-ttu-id="9b875-132">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="9b875-132">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="9b875-133">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="9b875-133">Configuring Cryptography Classes</span></span>](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
