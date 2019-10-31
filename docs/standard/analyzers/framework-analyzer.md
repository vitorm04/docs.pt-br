---
title: Os Analisadores de Segurança do .NET – .NET
description: Saiba como usar os Analisadores de Segurança do .NET no pacote de Analisadores do .NET Framework para localizar e corrigir riscos à segurança
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 03268375739b34a43f38c60fbfd2c993da9f3840
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197956"
---
# <a name="the-net-framework-analyzer"></a>O Analisador do .NET Framework

Você pode usar o Analisador do .NET Framework para localizar problemas potenciais no seu código de aplicativo baseado no .NET Framework. Este analisador localiza potenciais problemas e sugere correções para eles.

O analisador é executado interativamente no Visual Studio enquanto você escreve seu código ou como parte de um build de CI. Você deve adicionar o analisador ao seu projeto tão cedo quando possível no desenvolvimento. Quanto antes você encontrar potenciais problemas no seu código, mais fácil será corrigi-los. No entanto, você pode adicioná-lo a qualquer momento no ciclo de desenvolvimento. Ele encontra eventuais problemas com o código existente e avisa sobre novos problemas conforme você dá sequência ao desenvolvimento.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalar e configurar o Analisador do .NET Framework

Os Analisadores de Segurança do .NET devem ser instalados como um pacote do NuGet em cada projeto em que você deseja executá-los. Somente um desenvolvedor precisa adicioná-los ao projeto. O pacote de analisador é uma dependência de projeto e será executado no computador de cada um dos desenvolvedores assim que ele tiver a solução atualizada.

O Analisador do .NET Framework é fornecido no pacote do NuGet [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/). Esse pacote fornece apenas os analisadores específicos para o .NET Framework, que inclui os analisadores de segurança. Na maioria dos casos, você desejará o pacote do NuGet [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers). O pacote de agregação FxCopAnalyzers contém todos os analisadores de estrutura incluídos no pacote Framework.Analyzers, bem como os analisadores a seguir:

- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): fornece diretrizes gerais e diretrizes para APIs do .NET Standard
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): fornece analisadores específicos para as APIs do .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): fornece diretrizes para texto incluído como código, incluindo comentários.

Para instalá-lo, clique com o botão direito do mouse no projeto e selecione "Gerenciar Dependências".
Do explorador do NuGet, pesquise por "NetFramework Analyzer" ou, se você preferir, "Fx Cop Analyzer". Instale a versão estável mais recente em todos os projetos na solução.

## <a name="using-the-net-framework-analyzer"></a>Usar o Analisador do .NET Framework

Depois de instalar o pacote do NuGet, compile a solução. O analisador relatará eventuais problemas que ele localize na base de código. Os problemas são relatados como avisos na janela Lista de Erros do Visual Studio, conforme mostrado na imagem a seguir:

![problemas relatados pelo analisador de estrutura](./media/framework-analyzers-2.png)

Ao escrever código, você vê linhas onduladas sob qualquer problema potencial existente nele.
Passe o mouse sobre qualquer problema e você verá detalhes sobre o problema e sugestões de eventuais correções possíveis, conforme mostrado na imagem a seguir:

![relatório interativo de problemas encontrados pelo analisador de estrutura](./media/framework-analyzers-1.png)

Os analisadores examinam o código em sua solução e fornecem a você uma lista de avisos para qualquer um desses problemas:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: os tipos não devem estender determinados tipos base

Há um pequeno número de tipos do .NET Framework dos quais você não deve derivar diretamente. 

**Categoria:** design

**Severidade:** Aviso

Informações adicionais: [CA:1058: os tipos não devem estender determinados tipos base](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: não capturar exceções de estado corrompido

A captura de exceções de estado corrompido pode mascarar erros (como violações de acesso), resultando em um estado inconsistente de execução ou tornando mais fácil para invasores comprometerem um sistema. Em vez disso, capture e manipule um conjunto mais específico de tipos de exceção ou gere novamente a exceção

**Categoria:** segurança

**Severidade:** Aviso

Informações adicionais: [## CA2153: não capturar exceções de estado corrompido](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: implementar construtores de serialização

O analisador gera este aviso quando você cria um tipo que implementa a interface <xref:System.Runtime.Serialization.ISerializable>, mas não define o construtor de serialização necessário. Para corrigir uma violação dessa regra, implemente o construtor de serialização. Para uma classe lacrada, torne o construtor particular; do contrário, deixe-o protegido. O construtor de serialização tem a seguinte assinatura:

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

**Categoria:** uso

**Severidade:** Aviso

Informações adicionais: [CA2229: implementar construtores de serialização](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: marcar todos os campos não serializáveis

Um campo de instância de um tipo que não seja serializável é declarado em um tipo que é serializável. Você deve marcar explicitamente esse campo com o <xref:System.NonSerializedAttribute> para corrigir este aviso.

**Categoria:** uso

**Severidade:** Aviso

Informações adicionais: [CA2235: marcar todos os campos não serializáveis](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: marcar tipos ISerializable com serializable

Para serem reconhecidos pelo Common Language Runtime como serializáveis, os tipos devem ser marcados usando-se o atributo <xref:System.SerializableAttribute>, mesmo quando o tipo usa uma rotina de serialização personalizada implementando a interface <xref:System.Runtime.Serialization.ISerializable>.

**Categoria:** uso

**Severidade:** Aviso

Informações adicionais: [CA2237: marcar tipos ISerializable com serializable](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: processamento de DTD inseguro em XML

Se você usar instâncias de <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> inseguras ou referenciar origens de entidade externa, o analisador poderá aceitar a entrada não confiável e divulgar as informações confidenciais para invasores.  

**Categoria:** segurança

**Severidade:** Aviso

Informações adicionais: [A3075: processamento de DTD inseguro em XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: não usar algoritmos de criptografia fracos

Algoritmos de criptografia degradam-se ao longo do tempo, conforme os ataques se tornam mais avançados. Dependendo do tipo e do aplicativo desse algoritmo de criptografia, uma maior degradação de sua intensidade criptográfica poderá permitir que invasores leiam mensagens criptografadas, adulterem mensagens criptografadas, forjem assinaturas digitais, violem o conteúdo de hash ou comprometam qualquer sistema criptográfico baseado neste algoritmo. Para criptografia, use um algoritmo AES (AES-256, AES-192 e AES-128 são aceitáveis) com um comprimento de chave maior ou igual a 128 bits. Para o hash, use uma função de hash da família SHA-2, tal como SHA-2 512, SHA-2 384 ou SHA-2 256.

**Categoria:** segurança

**Severidade:** Aviso

Informações adicionais: [CA5350: não usar algoritmos de criptografia fracos](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: não usar algoritmos de criptografia violados

Existe um ataque que torna a quebra desse algoritmo computacionalmente viável. Isso permite que os invasores violem as garantias criptográficas que ele foi projetado para fornecer. Dependendo do tipo e do aplicativo desse algoritmo de criptografia, isso poderá permitir que invasores leiam e adulterem mensagens criptografadas, forjem assinaturas digitais, violem o conteúdo de hash ou comprometam qualquer sistema de criptografia baseado neste algoritmo. Para criptografia, use um algoritmo AES (AES-256, AES-192 e AES-128 são aceitáveis) com um comprimento de chave maior ou igual a 128 bits. Para o hash, use uma função de hash da família SHA-2, tal como SHA512, SHA384 ou SHA256. Para assinaturas digitais, use RSA com um comprimento de chave maior ou igual a 2.048 bits, ou então ECDSA com um comprimento de chave maior ou igual a 256 bits.

**Categoria:** segurança

**Severidade:** Aviso

Informações adicionais: [CA5351: não usar algoritmos de criptografia violados](/visualstudio/code-quality/ca5351)
