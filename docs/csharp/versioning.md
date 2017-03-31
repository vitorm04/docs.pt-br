---
title: "Controle de versão de C# | Guia de C#"
description: "Compreender o funcionamento do controle de versão em C# e .NET"
keywords: .NET, .NET Core, C#
author: tsolarin
manager: wpickett
ms.date: 01/08/2017
ms.topic: article
ms.prod: visual-studio-dev-14
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bfa94e6d994f63adb13bdeea9b23f7130799b438
ms.lasthandoff: 03/13/2017

---

# <a name="versioning-in-c"></a>Controle de versão em C# #

Neste tutorial, você aprenderá o que significa o controle de versão no .NET. Você também aprenderá os fatores a serem considerados ao fazer o controle de versão de sua biblioteca, bem como atualizar para uma nova versão da biblioteca.

## <a name="authoring-libraries"></a>Criando bibliotecas

Como um desenvolvedor que criou a bibliotecas .NET para uso público, provavelmente você esteve em situações em que precisa distribuir novas atualizações. Como você realiza esse processo é muito importante, pois você precisa garantir que haja uma transição suave do código existente para a nova versão da biblioteca. Aqui estão Vários aspectos a considerar ao criar uma nova versão:

### <a name="semantic-versioning"></a>Controle de Versão Semântico

[Controle de versão semântico](http://semver.org/) (SemVer, de forma abreviada) é uma convenção de nomenclatura aplicada a versões de sua biblioteca para indicar eventos com marcos específicos.
Idealmente, as informações de versão que você fornece a sua biblioteca devem ajudar os desenvolvedores a determinar a compatibilidade com seus projetos que usam versões mais antigas da mesma biblioteca.

A abordagem mais básica ao SemVer é o formato de 3 componentes `MAJOR.MINOR.PATCH`, em que:
 
* `MAJOR` é incrementado quando você faz alterações em APIs incompatíveis
* `MINOR` é incrementado quando você adiciona funcionalidades de maneira compatível com versões anteriores
* `PATCH` é incrementado quando você faz correções de bugs compatíveis com versões anteriores

Também há maneiras de especificar outros cenários, como versões de pré-lançamento etc. ao aplicar informações de versão à sua biblioteca .NET.

### <a name="backwards-compatibility"></a>Compatibilidade com versões anteriores

Conforme você lança novas versões de sua biblioteca, a compatibilidade com versões anteriores provavelmente será uma de suas principais preocupações.
Uma nova versão da biblioteca será compatível com a origem de uma versão anterior se o código que depende da versão anterior puder, quando recompilado, trabalhar com a nova versão. Uma nova versão da biblioteca será compatível de forma binária se um aplicativo que dependia da versão anterior puder, sem recompilação, trabalhar com a nova versão.

Aqui estão algumas coisas a serem consideradas ao tentar manter a compatibilidade com versões mais antigas de sua biblioteca:

* Métodos virtuais: quando você torna um método em virtual não virtual na nova versão, significa que projetos que substituem esse método precisarão ser atualizados. Essa é uma alteração muito grande e significativa que é altamente desaconselhável.
* Assinaturas de método: quando atualizar o comportamento de um método exigir que você altere também sua assinatura, você deve criar uma sobrecarga para que o código que chamar esse método ainda funcione.
Você sempre pode manipular a assinatura de método antiga para chamar a nova assinatura de método para que a implementação permaneça consistente.
* [Atributo obsoleto](programming-guide/concepts/attributes/common-attributes.md#Obsolete): você pode usar esse atributo no seu código para especificar classes ou membros da classe que foram preteridos e provavelmente serão removidos em versões futuras.
Isso garante que os desenvolvedores que utilizam sua biblioteca estarão melhor preparados para alterações significativas.
* Argumentos de método opcionais: quando você tornar argumentos de método que antes eram opcionais em compulsórios ou alterar seu valor padrão, todo código que não fornece esses argumentos precisará ser atualizado.
> [!NOTE]
> Tornar argumentos compulsórios em opcionais deve ter muito pouco efeito, especialmente se não alterar o comportamento do método.

Quanto mais fácil for para os usuários atualizarem para a nova versão da sua biblioteca, mais provável será que eles atualizem o quanto antes.

### <a name="application-configuration-file"></a>Arquivo de Configuração do Aplicativo

Como um desenvolvedor de .NET, há uma chance muito grande de você já ter encontrado o [arquivo o `app.config`](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx) na maioria dos tipos de projeto.
Esse arquivo de configuração simples pode fazer muita diferença para melhorar a distribuição de novas atualizações. Em geral, você deve projetar suas bibliotecas de forma que as informações que provavelmente serão alteradas regularmente sejam armazenadas no arquivo `app.config`. Dessa forma, quando essas informações forem atualizadas, o arquivo de configuração de versões mais antigas só precisa ser substituído pelo novo, sem a necessidade de recompilar a biblioteca.

## <a name="consuming-libraries"></a>Consumindo bibliotecas

Como um desenvolvedor que consome bibliotecas .NET criadas por outros desenvolvedores, vocês provavelmente está ciente de que uma nova versão de uma biblioteca pode não ser totalmente compatível com seu projeto e pode acabar precisando atualizar seu código para trabalhar com essas alterações.

Para sua sorte, o ecossistema do C# e do .NET tem recursos e técnicas que permitem facilmente atualizar nosso aplicativo para trabalhar com novas versões das bibliotecas que podem introduzir alterações significativas.

### <a name="assembly-binding-redirection"></a>Redirecionamento de associação de assembly

Você pode usar o arquivo `app.config` para atualizar a versão de uma biblioteca que seu aplicativo usa. Adicionando o que é chamado de [*redirecionamento de associação*](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx), você pode usar a nova versão da biblioteca sem ter que recompilar seu aplicativo. O exemplo a seguir mostra como atualizar o arquivo `app.config` de seu aplicativo para uso com a versão de patch `1.0.1` do `ReferencedLibrary` em vez da versão `1.0.0` com que ele foi compilado originalmente.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Essa abordagem só funcionará se a nova versão do `ReferencedLibrary` for compatível de forma binária com seu aplicativo.
> Consulte a seção [Compatibilidade com versões anteriores](#backwards-compatibility) acima para ver as alterações importantes ao determinar a compatibilidade.

### <a name="new"></a>new

Você usa o modificador `new` para ocultar membros herdados de uma classe base. Essa é uma maneira das classes derivadas responderem a atualizações em classes base.

Veja o exemplo a seguir:

[!code-csharp[Exemplo de uso do modificador "new"](../../samples/csharp/versioning/new/Program.cs#sample)]

**Saída**

```
A base method
A derived method
```

No exemplo acima, você pode ver como `DerivedClass` oculta o método `MyMethod` presente em `BaseClass`.
Isso significa que quando uma classe base na nova versão de uma biblioteca adiciona um membro que já existe em sua classe derivada, você pode simplesmente usar o modificador `new` no membro de sua classe derivada para ocultar o membro da classe base.

Quando nenhum modificador `new` é especificado, uma classe derivada ocultará por padrão membros conflitantes em uma classe base e, embora um aviso do compilador seja gerado, o código ainda será compilado. Isso significa que simplesmente adicionar novos membros a uma classe existente torna a nova versão da biblioteca compatível com a origem e de forma binária com o código que depende dela.

### <a name="override"></a>override

O modificador `override` significa que uma implementação derivada estende a implementação de um membro da classe base, em vez de ocultá-lo. O membro da classe base precisa ter o modificador `virtual` aplicado a ele.

[!code-csharp[Exemplo de uso do modificador "override"](../../samples/csharp/versioning/override/Program.cs#sample)]

**Saída**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

O modificador `override` é avaliado em tempo de compilação e o compilador gerará um erro se não encontrar um membro virtual para substituir.

Seu conhecimento sobre as técnicas discutidas, bem como sua compreensão das situações em que usá-las, farão muita diferença para facilitar a transição entre versões de uma biblioteca.

