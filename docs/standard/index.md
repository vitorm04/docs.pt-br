---
title: Sobre o .NET
description: Saiba mais sobre a plataforma .NET.
keywords: .NET, .NET Core
author: richlander
ms.author: ronpet
ms.date: 10/31/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: be44dce8181be45f6d73fcf498a873fb94aa56a6
ms.lasthandoff: 04/05/2017

---

# <a name="net-platform-guide"></a>Guia da plataforma .NET

> [!NOTE]
Este artigo será reescrito.

> Confira os [Tutoriais de "Introdução ao .NET Core"](../core/getting-started.md) para aprender a criar um aplicativo .NET Core simples. Bastam apenas alguns minutos para colocar seu primeiro aplicativo em funcionamento.

O .NET é uma plataforma de desenvolvimento de uso geral. Ele pode ser usado para qualquer espécie de tipo de aplicativo ou carga de trabalho em que as soluções de uso geral são utilizadas. Ele tem vários recursos-chave atraentes para muitos desenvolvedores, incluindo o gerenciamento automático de memória e linguagens de programação modernas, que facilitam a criação eficiente de aplicativos de alta qualidade. O .NET permite um ambiente de programação de alto nível com muitos recursos de conveniência, fornecendo acesso de baixo nível para memória nativa e APIs.

C#, F# e Visual Basic são linguagens populares que dependem da plataforma .NET e são direcionadas a ela. As linguagens do .NET são conhecidas por recursos importantes, como o modelo de programação assíncrona, consulta integrada à linguagem, tipos genéricos e reflexão tipo-sistema. As linguagens também fornecem excelentes opções tanto para paradigmas de programação funcional quanto voltada para objeto.

Há grande diversidade para essas linguagens na filosofia e na sintaxe, mas também há simetria fornecida por um sistema de tipo compartilhado. Esse sistema de tipo é fornecido pelo ambiente de tempo de execução subjacente. O .NET foi criado em torno da ideia de um "common language runtime" que pode dar suporte a requisitos de linguagens variadas – por exemplo, linguagens digitadas dinâmica e estaticamente – e permitir a interoperabilidade entre elas. Por exemplo, é possível passar uma coleção de `People` objetos entre diferentes idiomas sem perda de semântica ou funcionalidade.

Vários [produtos e implementações do .NET](components.md) estão disponíveis, com base em [padrões .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) de software livre que especificam os conceitos básicos da plataforma. Eles são separadamente otimizados para diferentes tipos de aplicativos (por exemplo, área de trabalho, móvel, jogos, nuvem) e suporte é dado a muitos chips (por exemplo, x86/x64, ARM) e sistemas operacionais (por exemplo, Windows, Linux, iOS, Android, macOS). Software livre também é uma parte importante do ecossistema do .NET, com várias implementações de .NET e muitas bibliotecas disponíveis sob licenças aprovadas OSI.

- Aprenda sobre o [C#](../csharp/index.md)
- Aprenda sobre o [F#](../fsharp/index.md)
- Pesquisar na [biblioteca de APIs do .NET](../../api/index.md)
- [Introdução ao Common Language Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/intro-to-clr.md)

<a name="fundamentals"></a>Princípios básicos
------------

**Várias Linguagens** – o .NET fornece um sistema de tipos, formatos de arquivo, tempo de execução, estrutura e ferramentas bem definidos que podem ser usadas por várias linguagens, tanto para sua própria de execução quanto para interoperação com outras linguagens usando os mesmos componentes do .NET como moeda compartilhada.

**Memória Gerenciada** – o .NET gerencia automaticamente a memória para você por meio de um coletor de lixo. Isso garante que você sempre referencie objetos em tempo real, assegurando que você evite problemas indesejáveis como estouros de buffer e violações de acesso. Isso inclui a verificação de limites de matriz.

**Segurança de Tipo** – O modelo primário do .NET para funcionalidade e representação de memória é "tipos". Tipos definem a forma e, opcionalmente, o comportamento. O tempo de execução garante que a chamada do código só possa operar em tipos que estejam de acordo com sua definição e com a visibilidade dos membros especificada, fornecendo resultados consistentes, confiáveis e seguros.

<a name="features"></a>Recursos
--------

**Tipos de valor definidos pelo usuário** – tipos de valor são uma categoria útil dos tipos, pois oferecem semântica de "passagem por valor de" em vez de "passagem por referência", assim como ocorre no caso de classes. A utilidade mais óbvia dos tipos de valor é para dados numéricos. O .NET permite tipos de valor tanto para tipos primitivos como inteiros quanto para tipos definidos pelo usuário.

**Tipos genéricos** – tipos genéricos são tipos com um ou mais parâmetros de tipo que podem ser especificados segundo a instanciação. Isso é útil para muitos tipos, que, normalmente, exporiam o conteúdo como o tipo de objeto ou exigiriam várias definições de tipo. Por exemplo, uma determinada instanciação de um tipo de coleção pode ser tornada específica às pessoas, locais de GPS ou cadeias de caracteres.

**Reflexão** – o .NET define um formato de metadados que descreve os tipos dentro de um binário. O subsistema de reflexão usa esses dados, expondo as APIs tanto para leitura quanto instanciação de tipos em tempo de execução. Esse recurso é muito útil para cenários dinâmicos nos quais não é conveniente conhecer a implementação exata de um programa antecipadamente.

**Geração de código flexível** – o .NET não estabelece uma abordagem específica para transformar os binários do .NET em código de computador. Muitas abordagens têm sido usadas com êxito, incluindo a interpretação, a compilação JIT (just-in-time), compilação AOT (Ahead Of Time) com fallback de JIT e compilação AOT sem fallback de JIT. Cada uma dessas estratégias pode ser valiosa e há oportunidades para usá-las em conjunto.

**Plataforma cruzada** – o .NET se destinava a ser de plataforma cruzada desde sua origem. O formato binário e o conjunto de instruções são independentes do sistema operacional, da CPU e do tamanho do ponteiro. Um determinado binário .NET compilado em 2000 para ser executado em um computador de 32 bits do Windows pode ser executado no dispositivo iOS ARM64 em 2016 sem modificações.

<a name="open-source"></a>Código Aberto
-----------

As implementações do [.NET Core](https://github.com/dotnet/core) e [Mono](https://github.com/mono/mono) são de software livre, usando a licença MIT. A documentação usa a licença [Creative Commons CC-BY](https://creativecommons.org/licenses/by/4.0/). .NET Core e Mono são patrocinados pela Microsoft e têm muitos colaboradores da comunidade. 

Esses tempos de execução para uso geral podem ser usados como a base de pesquisa acadêmica ou de aprendizado/ensino ou de produtos comerciais. Sua natureza de código livre também significa que qualquer pessoa pode contribuir com o código do produto upstream em caso de um bug ou se houver desejo de implementar um novo recurso.

<a name="projects"></a>Projetos
--------

- [CoreCLR](https://github.com/dotnet/coreclr) – tempo de execução do .NET, usado pelo .NET Core.
- [Mono](https://github.com/mono/mono) – tempo de execução do .NET, usado pelo Xamarin e outros.
- [CoreFX](https://github.com/dotnet/coreclr) – bibliotecas de classes do .NET, usado pelo .NET Core e até uma certa medida também pelo, Mono via compartilhamento de código-fonte.
- [Roslyn](https://github.com/dotnet/roslyn) – compiladores C# e Visual Basic, usados pela maioria das ferramentas e plataformas .NET. Expõe APIs para ler, gravar e analisar o código-fonte.
- [F#](https://github.com/microsoft/visualfsharp) – compilador F#.
- [SDK do Xamarin](http://open.xamarin.com) – ferramentas e bibliotecas necessárias para escrever macOS, iOS e Android em C# e F#.

<a name="standardized"></a>Padronizado
------------

O .NET é especificado por meio de [padrões ECMA](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) abertos que descrevem seus recursos e que podem ser usados para fazer uma nova implementação. Há outras implementações do .NET sendo que, depois daquelas da Microsoft, Mono e Unity são as mais populares.


