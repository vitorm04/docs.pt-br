---
title: Pacotes, Metapacotes e Estruturas
description: Pacotes, Metapacotes e Estruturas
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 609b0845-49e7-4864-957b-21ffe1b93bf2
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 2396b2794e88673afc1973b5bdd1e82c28fe5a13
ms.lasthandoff: 03/02/2017

---

# <a name="packages-metapackages-and-frameworks"></a>Pacotes, Metapacotes e Estruturas

O .NET Core é uma plataforma composta por pacotes NuGet. Algumas experiências de produtos aproveitam melhor a definição refinada de pacotes, enquanto para outros a alta granularidade é melhor. Para acomodar esse dualidade, o produto é distribuído como um conjunto refinado de pacotes, sendo então descrito como blocos mais volumosos com um tipo de pacote chamado informalmente de “metapacote”.

Cada um dos pacotes .NET Core dá suporte à execução de vários tempos de execução .NET, representados como estruturas. Algumas dessas estruturas são tradicionais, como o `net46`, que representa o .NET Framework. Outro conjunto são as novas estruturas que podem ser consideradas como "estruturas baseadas em pacote", que estabelecem um novo modelo para definir estruturas. Essas estruturas baseadas em pacote são totalmente formadas e definidas como pacotes, criando uma forte relação entre pacotes e estruturas.

## <a name="packages"></a>Pacotes

O .NET Core é dividido em um conjunto de pacotes, que fornecem tipos de dados primitivos de nível superior, tipos de composição de aplicativos e utilitários comuns. Cada um desses pacotes representa um único assembly de mesmo nome. Por exemplo, [System.Runtime](https://www.nuget.org/packages/System.Runtime) contém System.Runtime.dll. 

Há vantagens em definir pacotes de forma refinada:

- Pacotes refinados podem ser fornecidos em seu próprio cronograma, com testes relativamente limitados de outros pacotes.
- Pacotes refinados podem fornecer suporte a sistemas operacionais e CPUs diferentes.
- Pacotes refinados podem ter dependências específicas em apenas uma biblioteca.
- Os aplicativos são menores, pois os pacotes não referenciados não se tornam parte da distribuição do aplicativo.

Alguns desses benefícios são usados somente em determinadas circunstâncias. Por exemplo, pacotes .NET Core geralmente são fornecidos no mesmo cronograma que o suporte de plataforma. No caso de manutenção, as correções podem ser distribuídas e instaladas como atualizações de único pacote pequeno. Devido ao escopo restrito de alteração, a validação e o tempo para disponibilizar uma correção ficam limitados ao que é necessário para uma única biblioteca.

Veja a seguir uma lista dos principais pacotes NuGet para .NET Core:

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) – O pacote mais fundamental do .NET Core, incluindo [Object](http://docs.microsoft.com/dotnet/core/api/System.Object), [String](http://docs.microsoft.com/dotnet/core/api/System.String), [Array](http://docs.microsoft.com/dotnet/core/api/System.Array), [Action](http://docs.microsoft.com/dotnet/core/api/System.Action) e [IList&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1).
- [System.Collections](https://www.nuget.org/packages/System.Collections) – Um conjunto de coleções (primariamente) genéricas, incluindo [List&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) e [Dictionary&lt;K,V&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2).
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) – Um conjunto de tipos para comunicação de rede HTTP, incluindo [HttpClient](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpClient) e [HttpResponseMessage](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpResponseMessage).
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) – Um conjunto de tipos para leitura e gravação para o armazenamento de disco local ou em rede, incluindo [File](http://docs.microsoft.com/dotnet/core/api/System.IO.File) e [Directory](http://docs.microsoft.com/dotnet/core/api/System.IO.Directory).
- [System.Linq](https://www.nuget.org/packages/System.Linq) – Um conjunto de tipos para consultar os objetos, inclusive Enumerable e [ILookup&lt;TKey, TElement&gt;](http://docs.microsoft.com/dotnet/core/api/System.Linq.ILookup-2).
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) – Um conjunto de tipos para carregar, inspecionar e ativar tipos, incluindo [Assembly](http://docs.microsoft.com/dotnet/core/api/System.Reflection.Assembly), [TypeInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.TypeInfo) e [MethodInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.MethodInfo).

Os pacotes são referenciados no project.json. No exemplo abaixo, o [System.Runtime](https://www.nuget.org/packages/System.Runtime/) pacote é referenciado. 

```json
{
  "dependencies": {
    "System.Runtime": "4.1.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

Na maioria dos casos, você não fará referência a pacotes .NET Core de nível inferior diretamente, pois isso você acabaria com muitos pacotes para gerenciar. Em vez disso, você poderá fazer referência a um metapacote.

## <a name="metapackages"></a>Metapacotes

Metapacotes são uma convenção de pacotes NuGet para descrever um conjunto de pacotes que são significativos juntos. Eles representam esse conjunto de pacotes tornando-os dependências. Opcionalmente, eles podem estabelecer uma estrutura para esse conjunto de pacotes especificando-a. 

Ao referenciar um metapacote, você está efetivamente adicionando uma referência a cada um dos seus pacotes dependentes como um único gesto. Isso significa que todas as bibliotecas nesses pacotes (refs ou libs) estão disponíveis para o IntelliSense (ou experiência semelhante) e para publicação (somente libs) no seu aplicativo. 

Observação: os termos “lib” e “ref” referem-se a pastas em pacotes NuGet. Pastas “ref” descrevem a API pública de um pacote por meio de metadados do assembly. Pastas “lib” contêm a implementação dessa API pública para uma determinada estrutura. 

Há vantagens em usar metapacotes:

- Fornece uma experiência de usuário conveniente para fazer referência a um grande conjunto de pacotes refinados. 
- Define um conjunto de pacotes (incluindo versões específicas) que são testados e funcionam bem em conjunto.

O metapacote da .NET Standard Library:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) – Descreve as bibliotecas que fazem parte da “.NET Standard Library”. Aplica-se a todas as implementações do .NET (por exemplo, .NET Framework, .NET Core e Mono) que dão suporte à .NET Standard Library. Estabelece a estrutura “netstandard”.

Estes são os principais metapacotes .NET Core:

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) – Descreve as bibliotecas que fazem parte da distribuição do .NET Core. Estabelece a estrutura [`.NETCoreApp`](https://github.com/dotnet/core-setup/blob/master/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj). Conta com o `NETStandard.Library` menor.
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) – Um conjunto de fachadas de compatibilidade que permitem que PCLs (Bibliotecas de Classes Portáteis) baseadas em mscorlib sejam executadas no .NET Core.

Metapacotes são referenciados como qualquer outro pacote NuGet no project.json. 

No exemplo a seguir, o metapacote `NETStandard.Library` é referenciado, sendo usado para criar bibliotecas que são portáteis entre os tempos de execução do .NET.

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

No exemplo a seguir, o metapacote `Microsoft.NETCore.App` é referenciado, sendo usado para criar aplicativos e bibliotecas que devem ser executados no .NET Core e aproveitar todas as vantagens dele. Ele fornece acesso a um conjunto maior de bibliotecas do que o fornecido por `NETStandard.Library`.

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

## <a name="frameworks"></a>Estruturas

Cada pacote do .NET Core dá suporte a um conjunto de estruturas, declarado com as pastas da estrutura (dentro das pastas lib e ref mencionadas anteriormente). As estruturas descrevem um conjunto de APIs disponível (e possivelmente outras características) com os quais você pode contar ao direcionar uma determinada estrutura. Eles têm controle de versão à medida que novas APIs são adicionadas.

Por exemplo, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) dá suporte às seguintes estruturas:

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- Plataformas&6; Xamarin (por exemplo, xamarinios10)

É útil comparar essas duas primeiras estruturas, visto que elas são exemplos de duas formas diferentes de definir estruturas.

A estrutura `.NETFramework,Version=4.6` representa as APIs disponíveis no .NET Framework 4.6. Você pode gerar bibliotecas compiladas com os assemblies de referência do .NET Framework 4.6 e distribuí-las em pacotes NuGet em uma pasta lib net46. Ela será usada para aplicativos destinados ao .NET Framework 4.6 ou que são compatíveis com ele. Essa é a maneira como todas as estruturas tradicionalmente funcionam.

A estrutura `.NETStandard,Version=1.3` é uma estrutura baseada em pacote. Ela se baseia em pacotes direcionados para a estrutura definir e expor as APIs com relação à estrutura.

## <a name="package-based-frameworks"></a>Estruturas baseadas em pacote

Há uma relação bidirecional entre estruturas e pacotes. A primeira parte é definir as APIs disponíveis para uma determinada estrutura, por exemplo `netstandard1.3`. Pacotes direcionados a `netstandard1.3` (ou estruturas compatíveis, como o `netstandard1.0`) definem as APIs disponíveis para `netstandard1.3`. Isso pode parecer uma definição circular, mas não é. Por ser "baseada em pacote", a definição da API para a estrutura vem dos pacotes. A estrutura em si não define nenhuma APIs.

A segunda parte da relação é a seleção de ativo. Pacotes podem conter ativos para várias estruturas. Dada uma referência a um conjunto de pacotes e/ou metapacotes, a estrutura é necessária para determinar qual ativo será selecionado, por exemplo `net46` ou `netstandard1.3`. É importante selecionar o ativo correto. Por exemplo, um ativo `net46` provavelmente não é compatível com .NET Framework 4.0 ou .NET Core 1.0.

![Composição de estrutura baseada em pacote](./media/packages/package-framework.png)

Você pode ver essa relação na imagem acima. A *API* é voltada para a *estrutura* e a define. A *estrutura* é usada para *seleção de ativo*. O *ativo* fornece a API.

Uma questão interessante é imaginar onde a definição de uma estrutura baseada em pacote termina e onde começa o consumo dessa definição. Poderíamos considerar a exibição da estrutura como uma função de um determinado arquivo project.json. Suas dependências criam sua exibição da estrutura, independente dos fornecedores dessas dependências.

As duas principais estruturas baseadas em pacote usadas com o .NET Core são:

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

A estrutura .NET Standard (TFM: `netstandard`) representa as APIs definidas pela [.NET Standard Library](../standard/library.md) e criadas com base nela. Bibliotecas destinadas à execução em vários tempos de execução devem ter essa estrutura como destino. Elas terão suporte em qualquer tempo de execução compatível com.NET Standard, como .NET Core, .NET Framework e Mono/Xamarin. Cada um desses tempos de execução dá suporte a um conjunto de versões do .NET Standard, dependendo de quais APIs eles implementam. 

O metapacote `NETStandard.Library` é direcionado para a estrutura `netstandard`. A maneira mais comum de direcionar para `netstandard` é fazer referência a esse metapacote. Ele descreve e fornece acesso às ~40 bibliotecas .NET e APIs associadas, que definem a .NET Standard Library. Você pode referenciar outros pacotes destinados a `netstandard` para obter acesso a APIs adicionais.

Uma determinada [versão de NETStandard.Library](versions/index.md) coincide com a versão mais recente do `netstandard` exposta (por meio de seu fechamento). A referência da estrutura no project.json é usada para selecionar os ativos corretos dos pacotes subjacentes. Nesse caso, os ativos `netstandard1.6` são necessários, em vez de `netstandard1.4` ou `net46`, por exemplo. 

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

As referências de estrutura e metapacote no project.json não precisam corresponder. Por exemplo, o seguinte project.json é válido.

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.3": {}
  }
}
```

Pode parecer estranho apontar para `netstandard1.3`, mas use a versão 1.6.0 do `NETStandard.Library`. Esse é um caso de uso válido, pois o metapacote mantém o suporte para versões mais antigas do `netstandard`. Pode ser o caso de você já ter padronizado a versão 1.6.0 do metapacote e tê-la usado para todas as suas bibliotecas, que são voltadas para diversas versões do `netstandard`. Com essa abordagem, você só precisará restaurar a `NETStandard.Library` 1.6.0 e não versões anteriores. 

O inverso não seria válido: direcionar `netstandard1.6` com a versão 1.3.0 do `NETStandard.Library`. Você não pode direcionar uma estrutura mais elevada com um metapacote menos elevado, visto que a versão do metapacote inferior não exporá os ativos para essa estrutura superior. O [esquema de controle de versão] para metapacotes assegura que os metapacotes correspondam à versão mais alta da estrutura por eles descrita. Devido a esse esquema de controle de versão, a primeira versão do `NETStandard.Library` é v1.6.0, já que ele contém ativos `netstandard1.6`. A versão&1;.3.0 é usada no exemplo acima para fins de simetria, mas não existe na verdade.

### <a name="net-core-application"></a>.NET Core Application

A estrutura .NET Core Application (TFM: `netcoreapp`) representa os pacotes e APIs associadas que são fornecidos com a distribuição do .NET Core e o modelo de aplicativo de console que ela fornece. Aplicativos .NET Core devem usar essa estrutura, devido ao direcionamento do modelo de aplicativo de console, assim como as bibliotecas que devem ser executados apenas em .NET Core. Usar essa estrutura restringe a bibliotecas à execução apenas no .NET Core. 

O metapacote `Microsoft.NETCore.App` é direcionado para a estrutura `netcoreapp`. Ele fornece acesso a ~60 bibliotecas, ~&40; fornecida pelo pacote `NETStandard.Library` e mais ~20 adicionais. Você pode referenciar outras bibliotecas direcionadas ao `netcoreapp` ou estruturas compatíveis, como o `netstandard`, para obter acesso a APIs adicionais. 

A maioria das bibliotecas adicionais fornecidas pelo `Microsoft.NETCore.App` também são direcionadas para `netstandard`, considerando que suas dependências foram atendidas por outras bibliotecas `netstandard`. Isso significa que bibliotecas `netstandard` também podem fazer referência a esses pacotes como dependências. 
