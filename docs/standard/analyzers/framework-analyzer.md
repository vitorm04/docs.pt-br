---
title: "Os Analisadores de Segurança do .NET – .NET"
description: "Saiba como usar os Analisadores de Segurança do .NET no pacote de Analisadores do .NET Framework para localizar e corrigir riscos à segurança"
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 06a387d72d06609182c8894dd874b241a5d7b69c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2018
---
# <a name="the-net-framework-analyzer"></a><span data-ttu-id="43632-104">O Analisador do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43632-104">The .NET Framework Analyzer</span></span>

<span data-ttu-id="43632-105">Você pode usar o Analisador do .NET Framework para localizar problemas potenciais no seu código de aplicativo baseado no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43632-105">You can use the .NET Framework Analyzer to find potential issues in your .NET Framework-based application code.</span></span> <span data-ttu-id="43632-106">Este analisador localiza potenciais problemas e sugere correções para eles.</span><span class="sxs-lookup"><span data-stu-id="43632-106">This analyzer finds potential issues and suggests fixes to them.</span></span>

<span data-ttu-id="43632-107">O analisador é executado interativamente no Visual Studio enquanto você escreve seu código ou como parte de um build de CI.</span><span class="sxs-lookup"><span data-stu-id="43632-107">The analyzer runs interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="43632-108">Você deve adicionar o analisador ao seu projeto tão cedo quando possível no desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="43632-108">You should add the analyzer to your project as early as possible in your development.</span></span> <span data-ttu-id="43632-109">Quanto antes você encontrar potenciais problemas no seu código, mais fácil será corrigi-los.</span><span class="sxs-lookup"><span data-stu-id="43632-109">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="43632-110">No entanto, você pode adicioná-lo a qualquer momento no ciclo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="43632-110">However, you can add it at any time in the development cycle.</span></span> <span data-ttu-id="43632-111">Ele encontra eventuais problemas com o código existente e avisa sobre novos problemas conforme você dá sequência ao desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="43632-111">It finds any issues with the existing code and warns about new issues as you keep developing.</span></span>

## <a name="installing-and-configuring-the-net-framework-analyzer"></a><span data-ttu-id="43632-112">Instalar e configurar o Analisador do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43632-112">Installing and configuring the .NET Framework Analyzer</span></span>

<span data-ttu-id="43632-113">Os Analisadores de Segurança do .NET devem ser instalados como um pacote do NuGet em cada projeto em que você deseja executá-los.</span><span class="sxs-lookup"><span data-stu-id="43632-113">The .NET Security Analyzers must be installed as a NuGet package on every project where you want them to run.</span></span> <span data-ttu-id="43632-114">Somente um desenvolvedor precisa adicioná-los ao projeto.</span><span class="sxs-lookup"><span data-stu-id="43632-114">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="43632-115">O pacote de analisador é uma dependência de projeto e será executado no computador de cada um dos desenvolvedores assim que ele tiver a solução atualizada.</span><span class="sxs-lookup"><span data-stu-id="43632-115">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="43632-116">O Analisador do .NET Framework é fornecido no pacote do NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/).</span><span class="sxs-lookup"><span data-stu-id="43632-116">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="43632-117">Esse pacote fornece apenas os analisadores específicos para o .NET Framework, que inclui os analisadores de segurança.</span><span class="sxs-lookup"><span data-stu-id="43632-117">This package provides only the analyzers specific to the .NET Framework, which includes security analyzers.</span></span> <span data-ttu-id="43632-118">Na maioria dos casos, você desejará o pacote do NuGet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).</span><span class="sxs-lookup"><span data-stu-id="43632-118">In most cases, you'll want the [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet package.</span></span> <span data-ttu-id="43632-119">O pacote de agregação FxCopAnalyzers contém todos os analisadores de estrutura incluídos no pacote Framework.Analyzers, bem como os analisadores a seguir:</span><span class="sxs-lookup"><span data-stu-id="43632-119">The FxCopAnalyzers aggregate package contains all the framework analyzers included in the Framework.Analyzers package as well as the following analyzers:</span></span>
- <span data-ttu-id="43632-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): fornece diretrizes gerais e diretrizes para APIs do .NET Standard</span><span class="sxs-lookup"><span data-stu-id="43632-120">[Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Provides general guidance and guidance for .NET Standard APIs</span></span>
- <span data-ttu-id="43632-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): fornece analisadores específicos para as APIs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43632-121">[Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Provides analyzers specific to .NET Core APIs.</span></span>
- <span data-ttu-id="43632-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): fornece diretrizes para texto incluído como código, incluindo comentários.</span><span class="sxs-lookup"><span data-stu-id="43632-122">[Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Provides guidance for text included as code, including comments.</span></span>

<span data-ttu-id="43632-123">Para instalá-lo, clique com o botão direito do mouse no projeto e selecione "Gerenciar Dependências".</span><span class="sxs-lookup"><span data-stu-id="43632-123">To install it, right-click on the project, and select "Manage Dependencies".</span></span>
<span data-ttu-id="43632-124">Do explorador do NuGet, pesquise por "NetFramework Analyzer" ou, se você preferir, "Fx Cop Analyzer".</span><span class="sxs-lookup"><span data-stu-id="43632-124">From the NuGet explorer, search for "NetFramework Analyzer", or if you prefer, "Fx Cop Analyzer".</span></span> <span data-ttu-id="43632-125">Instale a versão estável mais recente em todos os projetos na solução.</span><span class="sxs-lookup"><span data-stu-id="43632-125">Install the latest stable version in all projects in your solution.</span></span>

## <a name="using-the-net-framework-analyzer"></a><span data-ttu-id="43632-126">Usar o Analisador do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="43632-126">Using the .NET Framework Analyzer</span></span>

<span data-ttu-id="43632-127">Depois de instalar o pacote do NuGet, compile a solução.</span><span class="sxs-lookup"><span data-stu-id="43632-127">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="43632-128">O analisador relatará eventuais problemas que ele localize na base de código.</span><span class="sxs-lookup"><span data-stu-id="43632-128">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="43632-129">Os problemas são relatados como avisos na janela Lista de Erros do Visual Studio, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="43632-129">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![problemas relatados pelo analisador de estrutura](./media/framework-analyzers-2.png)

<span data-ttu-id="43632-131">Ao escrever código, você vê linhas onduladas sob qualquer problema potencial existente nele.</span><span class="sxs-lookup"><span data-stu-id="43632-131">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="43632-132">Passe o mouse sobre qualquer problema e você verá detalhes sobre o problema e sugestões de eventuais correções possíveis, conforme mostrado na imagem a seguir:</span><span class="sxs-lookup"><span data-stu-id="43632-132">Hover over any issue and you see details about the issue, and suggestions for any possible fix, as shown in the following image:</span></span>

![relatório interativo de problemas encontrados pelo analisador de estrutura](./media/framework-analyzers-1.png)

<span data-ttu-id="43632-134">Os analisadores examinam o código em sua solução e fornecem a você uma lista de avisos para qualquer um desses problemas:</span><span class="sxs-lookup"><span data-stu-id="43632-134">The analyzers examine the code in your solution and provide you with a list of warnings for any of these issues:</span></span>

### <a name="ca1058-types-should-not-extend-certain-base-types"></a><span data-ttu-id="43632-135">CA1058: os tipos não devem estender determinados tipos base</span><span class="sxs-lookup"><span data-stu-id="43632-135">CA1058: Types should not extend certain base types</span></span>

<span data-ttu-id="43632-136">Há um pequeno número de tipos do .NET Framework dos quais você não deve derivar diretamente.</span><span class="sxs-lookup"><span data-stu-id="43632-136">There are a small number of types in the .NET Framework that you should not derived from directly.</span></span> 

<span data-ttu-id="43632-137">**Categoria:** design</span><span class="sxs-lookup"><span data-stu-id="43632-137">**Category:** Design</span></span>

<span data-ttu-id="43632-138">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-138">**Severity:** Warning</span></span>

<span data-ttu-id="43632-139">Informações adicionais: [CA:1058: os tipos não devem estender determinados tipos base](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span><span class="sxs-lookup"><span data-stu-id="43632-139">Additional information: [CA:1058: Types should not extend certain base types](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)</span></span>

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a><span data-ttu-id="43632-140">CA2153: não capturar exceções de estado corrompido</span><span class="sxs-lookup"><span data-stu-id="43632-140">CA2153: Do not catch corrupted state exceptions</span></span>

<span data-ttu-id="43632-141">A captura de exceções de estado corrompido pode mascarar erros (como violações de acesso), resultando em um estado inconsistente de execução ou tornando mais fácil para invasores comprometerem um sistema.</span><span class="sxs-lookup"><span data-stu-id="43632-141">Catching corrupted state exceptions could mask errors (such as access violations), resulting in an inconsistent state of execution or making it easier for attackers to compromise a system.</span></span> <span data-ttu-id="43632-142">Em vez disso, capture e manipule um conjunto mais específico de tipos de exceção ou gere novamente a exceção</span><span class="sxs-lookup"><span data-stu-id="43632-142">Instead, catch and handle a more specific set of exception type(s) or re-throw the exception</span></span>

<span data-ttu-id="43632-143">**Categoria:** segurança</span><span class="sxs-lookup"><span data-stu-id="43632-143">**Category:** Security</span></span>

<span data-ttu-id="43632-144">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-144">**Severity:** Warning</span></span>

<span data-ttu-id="43632-145">Informações adicionais: [## CA2153: não capturar exceções de estado corrompido](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span><span class="sxs-lookup"><span data-stu-id="43632-145">Additional information: [## CA2153: Do not catch corrupted state exceptions](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)</span></span>

### <a name="ca2229-implement-serialization-constructors"></a><span data-ttu-id="43632-146">CA2229: implementar construtores de serialização</span><span class="sxs-lookup"><span data-stu-id="43632-146">CA2229: Implement serialization constructors</span></span>

<span data-ttu-id="43632-147">O analisador gera este aviso quando você cria um tipo que implementa a interface <xref:System.Runtime.Serialization.ISerializable>, mas não define o construtor de serialização necessário.</span><span class="sxs-lookup"><span data-stu-id="43632-147">The analyzer generates this warning when you create a type that implements the <xref:System.Runtime.Serialization.ISerializable> interface but does not define the required serialization constructor.</span></span> <span data-ttu-id="43632-148">Para corrigir uma violação dessa regra, implemente o construtor de serialização.</span><span class="sxs-lookup"><span data-stu-id="43632-148">To fix a violation of this rule, implement the serialization constructor.</span></span> <span data-ttu-id="43632-149">Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido.</span><span class="sxs-lookup"><span data-stu-id="43632-149">For a sealed class, make the constructor private; otherwise, make it protected.</span></span> <span data-ttu-id="43632-150">O construtor de serialização tem a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="43632-150">The serialization constructor has the following signature:</span></span>

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

<span data-ttu-id="43632-151">**Categoria:** uso</span><span class="sxs-lookup"><span data-stu-id="43632-151">**Category:** Usage</span></span>

<span data-ttu-id="43632-152">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-152">**Severity:** Warning</span></span>

<span data-ttu-id="43632-153">Informações adicionais: [CA2229: implementar construtores de serialização](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span><span class="sxs-lookup"><span data-stu-id="43632-153">Additional information: [CA2229: Implement serialization constructors](/visualstudio/code-quality/ca2229-implement-serialization-constructors)</span></span>

### <a name="ca2235-mark-all-non-serializable-fields"></a><span data-ttu-id="43632-154">CA2235: marcar todos os campos não serializáveis</span><span class="sxs-lookup"><span data-stu-id="43632-154">CA2235: Mark all non-serializable fields</span></span>

<span data-ttu-id="43632-155">Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável.</span><span class="sxs-lookup"><span data-stu-id="43632-155">An instance field of a type that is not serializable is declared in a type that is serializable.</span></span> <span data-ttu-id="43632-156">Você deve marcar explicitamente esse campo com o <xref:System.NonSerializedAttribute> para corrigir este aviso.</span><span class="sxs-lookup"><span data-stu-id="43632-156">You must explicitly mark that field with the <xref:System.NonSerializedAttribute> to fix this warning.</span></span>

<span data-ttu-id="43632-157">**Categoria:** uso</span><span class="sxs-lookup"><span data-stu-id="43632-157">**Category:** Usage</span></span>

<span data-ttu-id="43632-158">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-158">**Severity:** Warning</span></span>

<span data-ttu-id="43632-159">Informações adicionais: [CA2235: marcar todos os campos não serializáveis](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span><span class="sxs-lookup"><span data-stu-id="43632-159">Additional information: [CA2235: Mark all non-serializable fields](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)</span></span>

### <a name="ca2237-mark-iserializable-types-with-serializable"></a><span data-ttu-id="43632-160">CA2237: marcar tipos ISerializable com serializable</span><span class="sxs-lookup"><span data-stu-id="43632-160">CA2237: Mark ISerializable types with serializable</span></span>

<span data-ttu-id="43632-161">Para serem reconhecidos pelo Common Language Runtime como serializáveis, os tipos devem ser marcados usando-se o atributo <xref:System.SerializableAttribute>, mesmo quando o tipo usa uma rotina de serialização personalizada implementando a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="43632-161">To be recognized by the common language runtime as serializable, types must be marked by using the <xref:System.SerializableAttribute> attribute even when the type uses a custom serialization routine by implementing the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

<span data-ttu-id="43632-162">**Categoria:** uso</span><span class="sxs-lookup"><span data-stu-id="43632-162">**Category:** Usage</span></span>

<span data-ttu-id="43632-163">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-163">**Severity:** Warning</span></span>

<span data-ttu-id="43632-164">Informações adicionais: [CA2237: marcar tipos ISerializable com serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="43632-164">Additional information: [CA2237: Mark ISerializable types with serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>

### <a name="ca3075-insecure-dtd-processing-in-xml"></a><span data-ttu-id="43632-165">CA3075: processamento de DTD inseguro em XML</span><span class="sxs-lookup"><span data-stu-id="43632-165">CA3075: Insecure DTD processing in XML</span></span>

<span data-ttu-id="43632-166">Se você usar instâncias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> inseguras ou referenciar origens de entidade externa, o analisador poderá aceitar a entrada não confiável e divulgar as informações confidenciais para invasores.</span><span class="sxs-lookup"><span data-stu-id="43632-166">If you use insecure <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instances or reference external entity sources, the parser may accept untrusted input and disclose sensitive information to attackers.</span></span>  

<span data-ttu-id="43632-167">**Categoria:** segurança</span><span class="sxs-lookup"><span data-stu-id="43632-167">**Category:** Security</span></span>

<span data-ttu-id="43632-168">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-168">**Severity:** Warning</span></span>

<span data-ttu-id="43632-169">Informações adicionais: [A3075: processamento de DTD inseguro em XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span><span class="sxs-lookup"><span data-stu-id="43632-169">Additional information: [A3075: Insecure DTD processing in XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)</span></span>


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a><span data-ttu-id="43632-170">CA5350: não usar algoritmos de criptografia fracos</span><span class="sxs-lookup"><span data-stu-id="43632-170">CA5350: Do not use weak cryptographic algorithms</span></span>

<span data-ttu-id="43632-171">Algoritmos de criptografia degradam-se ao longo do tempo, conforme os ataques se tornam mais avançados.</span><span class="sxs-lookup"><span data-stu-id="43632-171">Cryptographic algorithms degrade over time as attacks become more advanced.</span></span> <span data-ttu-id="43632-172">Dependendo do tipo e do aplicativo desse algoritmo de criptografia, uma maior degradação de sua intensidade criptográfica poderá permitir que invasores leiam mensagens criptografadas, adulterem mensagens criptografadas, forjem assinaturas digitais, violem o conteúdo de hash ou comprometam qualquer sistema criptográfico baseado neste algoritmo.</span><span class="sxs-lookup"><span data-stu-id="43632-172">Depending on the type and application of this cryptographic algorithm, further degradation of its cryptographic strength may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="43632-173">Para criptografia, use um algoritmo AES (AES-256, AES-192 e AES-128 são aceitáveis) com um comprimento de chave maior ou igual a 128 bits.</span><span class="sxs-lookup"><span data-stu-id="43632-173">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="43632-174">Para o hash, use uma função de hash da família SHA-2, tal como SHA-2 512, SHA-2 384 ou SHA-2 256.</span><span class="sxs-lookup"><span data-stu-id="43632-174">For hashing, use a hashing function in the SHA-2 family, such as SHA-2 512, SHA-2 384, or SHA-2 256.</span></span>

<span data-ttu-id="43632-175">**Categoria:** segurança</span><span class="sxs-lookup"><span data-stu-id="43632-175">**Category:** Security</span></span>

<span data-ttu-id="43632-176">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-176">**Severity:** Warning</span></span>

<span data-ttu-id="43632-177">Informações adicionais: [CA5350: não usar algoritmos de criptografia fracos](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="43632-177">Additional information: [CA5350: Do not use weak cryptographic algorithms](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)</span></span>

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a><span data-ttu-id="43632-178">CA5351: não usar algoritmos de criptografia violados</span><span class="sxs-lookup"><span data-stu-id="43632-178">CA5351: Do not use broken cryptographic algorithms</span></span>

<span data-ttu-id="43632-179">Existe um ataque que torna a quebra desse algoritmo computacionalmente viável.</span><span class="sxs-lookup"><span data-stu-id="43632-179">An attack making it computationally feasible to break this algorithm exists.</span></span> <span data-ttu-id="43632-180">Isso permite que os invasores violem as garantias criptográficas que ele foi projetado para fornecer.</span><span class="sxs-lookup"><span data-stu-id="43632-180">This allows attackers to break the cryptographic guarantees it is designed to provide.</span></span> <span data-ttu-id="43632-181">Dependendo do tipo e do aplicativo desse algoritmo de criptografia, isso poderá permitir que invasores leiam e adulterem mensagens criptografadas, forjem assinaturas digitais, violem o conteúdo de hash ou comprometam qualquer sistema de criptografia baseado neste algoritmo.</span><span class="sxs-lookup"><span data-stu-id="43632-181">Depending on the type and application of this cryptographic algorithm, this may allow attackers to read enciphered messages, tamper with enciphered messages, forge digital signatures, tamper with hashed content, or otherwise compromise any cryptosystem based on this algorithm.</span></span> <span data-ttu-id="43632-182">Para criptografia, use um algoritmo AES (AES-256, AES-192 e AES-128 são aceitáveis) com um comprimento de chave maior ou igual a 128 bits.</span><span class="sxs-lookup"><span data-stu-id="43632-182">For encryption, use an AES algorithm (AES-256, AES-192 and AES-128 are acceptable) with a key length greater than or equal to 128 bits.</span></span> <span data-ttu-id="43632-183">Para o hash, use uma função de hash da família SHA-2, tal como SHA512, SHA384 ou SHA256.</span><span class="sxs-lookup"><span data-stu-id="43632-183">For hashing, use a hashing function in the SHA-2 family, such as SHA512, SHA384, or SHA256.</span></span> <span data-ttu-id="43632-184">Para assinaturas digitais, use RSA com um comprimento de chave maior ou igual a 2.048 bits, ou então ECDSA com um comprimento de chave maior ou igual a 256 bits.</span><span class="sxs-lookup"><span data-stu-id="43632-184">For digital signatures, use RSA with a key length greater than or equal to 2048-bits, or ECDSA with a key length greater than or equal to 256 bits.</span></span>

<span data-ttu-id="43632-185">**Categoria:** segurança</span><span class="sxs-lookup"><span data-stu-id="43632-185">**Category:** Security</span></span>

<span data-ttu-id="43632-186">**Severidade:** Aviso</span><span class="sxs-lookup"><span data-stu-id="43632-186">**Severity:** Warning</span></span>

<span data-ttu-id="43632-187">Informações adicionais: [CA5351: não usar algoritmos de criptografia violados](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span><span class="sxs-lookup"><span data-stu-id="43632-187">Additional Information: [CA5351: Do not use broken cryptographic algorithms](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)</span></span>


