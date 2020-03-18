---
title: Entendendo AssemblyLoadContext - .NET Core
description: Conceitos-chave para entender o propósito e o comportamento do AssemblyLoadContext no .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72291256"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Entendendo System.Runtime.Loader.AssemblyLoadContext

A <xref:System.Runtime.Loader.AssemblyLoadContext> classe é exclusiva do .NET Core. Este artigo tenta <xref:System.Runtime.Loader.AssemblyLoadContext> complementar a documentação da API com informações conceituais.

Este artigo é relevante para desenvolvedores que implementam carregamento dinâmico, especialmente desenvolvedores de estruturas de carregamento dinâmico.

## <a name="what-is-the-assemblyloadcontext"></a>O que é o AssemblyLoadContext?

Cada aplicativo .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext>usa implicitamente o .
É o provedor de tempo de execução para localizar e carregar dependências. Sempre que uma dependência é <xref:System.Runtime.Loader.AssemblyLoadContext> carregada, uma instância é invocada para localizá-la.

- Ele fornece um serviço de localização, carregamento e cache de conjuntos gerenciados e outras dependências.

- Para suportar o carregamento e descarga de códigodinâmico, ele cria um <xref:System.Runtime.Loader.AssemblyLoadContext> contexto isolado para o código de carregamento e suas dependências em sua própria instância.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Quando você precisa de várias instâncias assemblyLoadContext?

Uma <xref:System.Runtime.Loader.AssemblyLoadContext> única instância está limitada a <xref:System.Reflection.Assembly> carregar exatamente uma <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>versão de um nome de montagem simples, .

Essa restrição pode se tornar um problema ao carregar módulos de código dinamicamente. Cada módulo é compilado independentemente e pode <xref:System.Reflection.Assembly>depender de versões diferentes de um . Esse problema geralmente ocorre quando diferentes módulos dependem de versões diferentes de uma biblioteca comumente usada.

Para suportar o código <xref:System.Runtime.Loader.AssemblyLoadContext> de carregamento dinâmico, a API prevê o carregamento de versões conflitantes de um <xref:System.Reflection.Assembly> no mesmo aplicativo. Cada <xref:System.Runtime.Loader.AssemblyLoadContext> instância fornece um <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> mapeamento de <xref:System.Reflection.Assembly> dicionário único para uma instância específica.

Ele também fornece um mecanismo conveniente para agrupar dependências relacionadas a um módulo de código para descarregar posteriormente.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>O que há de especial na instância AssemblyLoadContext.Default?

A <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instância é preenchida automaticamente pelo tempo de execução na inicialização.  Ele usa [sondagem padrão](default-probing.md) para localizar e encontrar todas as dependências estáticas.

Resolve os cenários de carregamento de dependência mais comuns.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Como o AssemblyLoadContext suporta dependências dinâmicas?

<xref:System.Runtime.Loader.AssemblyLoadContext>tem vários eventos e funções virtuais que podem ser substituídos.

A <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> instância só suporta sobrepor os eventos.

Os artigos [Algoritmo de carregamento de montagem gerenciado,](loading-managed.md)algoritmo de carregamento de montagem de [satélite](loading-resources.md)e algoritmo de carregamento de biblioteca não [gerenciado (nativo)](loading-unmanaged.md) referem-se a todos os eventos e funções virtuais disponíveis.  Os artigos mostram a posição relativa de cada evento e função nos algoritmos de carregamento. Este artigo não reproduz essa informação.

Esta seção abrange os princípios gerais para os eventos e funções relevantes.

- **Seja repetível**. Uma consulta para uma dependência específica deve sempre resultar na mesma resposta. A mesma instância de dependência carregada deve ser devolvida. Esse requisito é fundamental para a consistência do cache. Para montagens gerenciadas em particular, <xref:System.Reflection.Assembly> estamos criando um cache. A chave de cache é <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>um nome de montagem simples, .
- **Normalmente não jogam.**  Espera-se que essas funções retornem `null` em vez de serem jogadas quando não conseguem encontrar a dependência solicitada. O arremesso acabará prematuramente com a busca e será propagado uma exceção ao interlocutor. O arremesso deve ser restrito a erros inesperados, como um conjunto corrompido ou uma condição fora da memória.
- **Evite a recursão.** Esteja ciente de que essas funções e manipuladores implementam as regras de carregamento para localizar dependências. Sua implementação não deve chamar APIs que acionam a recursão. Seu código normalmente deve chamar funções de carga **AssemblyLoadContext** que requerem um argumento específico de referência de caminho ou memória.
- **Carregar no AssemblyLoadContext correto**. A escolha de onde carregar dependências é específica do aplicativo.  A escolha é implementada por esses eventos e funções. Quando o código chama as funções de carga por caminho **AssemblyLoadContext,** chame-as na instância em que você deseja que o código seja carregado. Em algum `null` momento, <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> retornar e deixar o cabo da carga pode ser a opção mais simples.
- **Esteja atento às corridas de linha.** O carregamento pode ser acionado por vários segmentos. O AssemblyLoadContext lida com corridas de segmento adicionando atomicamente conjuntos ao seu cache. A instância do perdedor da corrida está descartada. Em sua lógica de implementação, não adicione lógica extra que não manuseie vários segmentos corretamente.

## <a name="how-are-dynamic-dependencies-isolated"></a>Como as dependências dinâmicas são isoladas?

Cada <xref:System.Runtime.Loader.AssemblyLoadContext> instância representa um <xref:System.Reflection.Assembly> escopo <xref:System.Type> único para instâncias e definições.

Não há isolamento binário entre essas dependências. Eles só estão isolados por não se encontrarem pelo nome.

Em <xref:System.Runtime.Loader.AssemblyLoadContext>cada um:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>pode se referir <xref:System.Reflection.Assembly> a uma instância diferente.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>pode retornar uma instância de `name`tipo diferente para o mesmo tipo .

## <a name="how-are-dependencies-shared"></a>Como as dependências são compartilhadas?

As dependências podem ser <xref:System.Runtime.Loader.AssemblyLoadContext> facilmente compartilhadas entre instâncias. O modelo geral <xref:System.Runtime.Loader.AssemblyLoadContext> é para se carregar uma dependência.  O outro compartilha a dependência usando uma referência ao conjunto carregado.

Este compartilhamento é necessário para as assembléias em tempo de execução. Estas assembléias só podem <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>ser carregadas no . O mesmo é necessário `ASP.NET`para `WPF`estruturas `WinForms`como, ou .

Recomenda-se que as dependências compartilhadas sejam <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>carregadas em . Esse compartilhamento é o padrão de design comum.

O compartilhamento é implementado na <xref:System.Runtime.Loader.AssemblyLoadContext> codificação da instância personalizada. <xref:System.Runtime.Loader.AssemblyLoadContext>tem vários eventos e funções virtuais que podem ser substituídos. Quando qualquer uma dessas funções <xref:System.Reflection.Assembly> retorna uma referência a <xref:System.Runtime.Loader.AssemblyLoadContext> uma <xref:System.Reflection.Assembly> instância que foi carregada em outra instância, a instância é compartilhada. O algoritmo de carga <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> padrão adia para o carregamento para simplificar o padrão de compartilhamento comum.  Consulte [algoritmo de carregamento de montagem gerenciado](loading-managed.md).

## <a name="complications"></a>Complicações

### <a name="type-conversion-issues"></a>Problemas de conversão de tipo

Quando <xref:System.Runtime.Loader.AssemblyLoadContext> duas instâncias contêm `name`definições de tipo com o mesmo, elas não são do mesmo tipo. Eles são do mesmo tipo se e somente <xref:System.Reflection.Assembly> se eles vêm da mesma instância.

Para complicar as coisas, mensagens de exceção sobre esses tipos incompatíveis podem ser confusas. Os tipos são referidos nas mensagens de exceção por seus nomes de tipos simples. A mensagem de exceção comum neste caso seria do formulário:

> O objeto do tipo 'IsolatedType' não pode ser convertido para digitar 'IsolatedType'.

### <a name="debugging-type-conversion-issues"></a>Problemas de conversão de tipo de depuração

Dado um par de tipos incompatíveis, é importante também saber:

- Cada tipo<xref:System.Type.Assembly?displayProperty=nameWithType>
- Cada tipo <xref:System.Runtime.Loader.AssemblyLoadContext>é, que pode ser <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> obtido através da função.

Dado `a` dois `b`objetos e, avaliando o seguinte no depurador será útil:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Resolução de problemas de conversão de tipo

Existem dois padrões de design para resolver esses problemas de conversão de tipo.

1. Use tipos comuns compartilhados. Este tipo compartilhado pode ser um tipo primitivo de tempo de execução, ou pode envolver a criação de um novo tipo compartilhado em um conjunto compartilhado.  Muitas vezes, o tipo compartilhado é uma [interface](../../csharp/language-reference/keywords/interface.md) definida em um conjunto de aplicativos. Veja também: [Como as dependências são compartilhadas?](#how-are-dependencies-shared).

2. Use técnicas de empacotamento para converter de um tipo para outro.
