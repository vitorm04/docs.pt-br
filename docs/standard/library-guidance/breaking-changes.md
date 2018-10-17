---
title: Alterações significativas e bibliotecas do .NET
description: Práticas recomendadas para navegar em alterações significativas ao criar bibliotecas .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369681"
---
# <a name="breaking-changes"></a>Alterações significativas

É importante para uma biblioteca .NET encontrar um equilíbrio entre a estabilidade para usuários existentes e a inovação para o futuro. Autores de biblioteca de lean na direção de refatoração e repensar o código até que ele é perfeito, mas quebra a seus usuários existentes tem um impacto negativo, especialmente para bibliotecas de baixo nível.

## <a name="project-types-and-breaking-changes"></a>Tipos de projeto e as alterações recentes

Como uma biblioteca é usada pela comunidade .NET altera o efeito das alterações significativas nos desenvolvedores do usuário final.

* **Bibliotecas de nível médio e baixo** como um serializador, analisador HTML, mapeador relacional de objeto de banco de dados ou estrutura da web são mais afetados por alterações significativas.

  Bloco de construção de pacotes são usados por desenvolvedores do usuário final para criar aplicativos e por outras bibliotecas como dependências do NuGet. Por exemplo, você estiver criando um aplicativo e estiver usando um cliente de software livre para chamar um serviço web. Uma atualização significativa para uma dependência que o cliente usa não é algo que você pode corrigir. É o cliente de software livre que precisa ser alterado e você não tem controle sobre ele. Você precisa localizar as versões compatíveis das bibliotecas ou enviar uma correção para a biblioteca de cliente e aguarde até que uma nova versão. A pior situação é se você deseja usar duas bibliotecas que dependem de versões mutuamente incompatíveis de uma biblioteca de terceiro.

* **Bibliotecas de alto nível** como um pacote de interface do usuário controles são menos sensíveis a alterações significativas.

  Bibliotecas de alto nível são referenciadas diretamente em um aplicativo do usuário final. Se ocorrerem alterações significativas, o desenvolvedor pode optar por atualizar para a versão mais recente, ou pode modificar seu aplicativo para trabalhar com a alteração significativa.

**FAZER ✔️** pense em como sua biblioteca será usada. Efeito de alterações significativas terão em aplicativos e bibliotecas que usá-lo?

**FAZER ✔️** minimizar alterações significativas ao desenvolver uma biblioteca .NET de nível inferior.

**Considere a possibilidade de ✔️** publicando um principal de reconfiguração de uma biblioteca como um novo pacote do NuGet.

## <a name="types-of-breaking-changes"></a>Tipos de alterações significativas

Alterações interruptivas se enquadram nas categorias diferentes e não são igualmente impactantes.

### <a name="source-breaking-change"></a>Alteração significativa de código-fonte

Uma alteração significativa de fonte não afeta a execução do programa, mas causará erros de compilação na próxima vez que o aplicativo for recompilado. Por exemplo, uma nova sobrecarga pode criar ambiguidade em chamadas de método que antes estavam inequívocas, ou um parâmetro renomeado interromperá os chamadores que usam parâmetros nomeados.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Como uma fonte de alteração significativa é prejudicial somente quando os desenvolvedores recompilar seus aplicativos, é a alteração significativa com menos interrupções. Os desenvolvedores podem corrigir facilmente seu próprio código de origem quebrado.

### <a name="behavior-breaking-change"></a>Alteração de comportamento de quebra

Alterações de comportamento são o tipo mais comum de alteração interruptiva: quase qualquer alteração no comportamento poderia interromper alguém. Alterações na sua biblioteca, como assinaturas de método, as exceções geradas ou entrada ou saída formatos de dados, todos os pode afetar negativamente seus consumidores de biblioteca. Até mesmo uma correção de bug pode se qualificar como uma alteração significativa se os usuários contavam com o comportamento desfeito anteriormente.

Adicionando recursos e melhorando a maus comportamentos são uma coisa boa, mas sem cuidado ele pode facilitar muito difícil para os usuários existentes para atualizar. Uma abordagem para ajudar os desenvolvedores a lidar com alterações significativas de comportamento é para ocultá-los por trás de configurações. As configurações permitem que os desenvolvedores a atualizar para a versão mais recente da sua biblioteca enquanto ao mesmo tempo optando por aceitar ou recusar alterações significativas. Essa estratégia permite que os desenvolvedores a se manter atualizado, permitindo que seu código de consumo adaptar-se ao longo do tempo.

Por exemplo, o ASP.NET Core MVC tem o conceito de um [versão de compatibilidade](/aspnet/core/mvc/compatibility-version) que modifica os recursos habilitados e desabilitados em `MvcOptions`.

**Considere a possibilidade de ✔️** omitindo novos recursos por padrão, se eles afetam os usuários existentes e permitir que os desenvolvedores a aceitar o recurso com uma configuração.

### <a name="binary-breaking-change"></a>Alteração significativa binário

Um binário alteração significativa acontece quando você altera a API pública de sua biblioteca, portanto, os assemblies compilados em relação a versões mais antigas da sua biblioteca não são mais capazes de chamar a API. Por exemplo, a alteração de assinatura de um método, adicionando um novo parâmetro fará com que assemblies compilados com a versão mais antiga da biblioteca lançar um <xref:System.MissingMethodException>.

Um alteração significativa de binário também pode interromper uma **assembly inteiro**. Renomeando um assembly com `AssemblyName` alterará a identidade do assembly, assim como adicionar, remover ou alterar a chave de nomenclatura forte do assembly. Uma alteração de identidade de um assembly interromperá todo o código compilado que o utiliza.

**❌ NÃO** alterar um nome de assembly.

**❌ NÃO** adicionar, remover ou alterar a chave de nomeação forte.

**Considere a possibilidade de ✔️** usando classes base abstratas, em vez de interfaces.

> Adicionar algo para uma interface fará com que os tipos existentes que implementam a falha. Uma classe base abstrata permite que você adicione uma implementação de virtual padrão.

**Considere a possibilidade de ✔️** colocando o <xref:System.ObsoleteAttribute> nos tipos e membros que você pretende remover. O atributo deve ter instruções para atualizar o código não for mais usar a API obsoleta.

> Código que chama os tipos e métodos com o <xref:System.ObsoleteAttribute> gerará um aviso de compilação com a mensagem fornecida para o atributo. As avisos oferecem as pessoas que usam o tempo de superfície de API obsoleto para migrar para que quando a API obsoleta é removida, a maioria não é mais usá-lo.

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

## <a name="see-also"></a>Consulte também

* [Considerações sobre versão e atualização para os desenvolvedores de c#](../../csharp/whats-new/version-update-considerations.md)
* [Um guia definitivo para as alterações recentes de API do .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [Regras de alteração de quebra do CoreFX](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[Anterior](./versioning.md)
