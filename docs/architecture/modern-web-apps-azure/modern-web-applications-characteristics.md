---
title: Características de aplicativos Web modernos
description: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Características de aplicativos Web modernos
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: d70fa54adeb505fd37807399402281dfda67cf52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451558"
---
# <a name="characteristics-of-modern-web-applications"></a>Características de aplicativos Web modernos

> "… com o design correto, os recursos são obtidos sem esforços. Essa abordagem é árdua, mas continua a ter êxito."  
> _\-Dennis Ritchie_

Os aplicativos Web modernos têm maiores expectativas de usuário e maiores demandas do que nunca. Os aplicativos Web de hoje devem estar disponíveis 24/7 em qualquer lugar do mundo e ser utilizáveis praticamente em qualquer dispositivo ou tamanho de tela. Os aplicativos Web precisam ser seguros, flexíveis e escalonáveis para atender aos picos da demanda. Cada vez mais, os cenários complexos devem ser tratados por experiências avançadas do usuário criadas no cliente por meio de JavaScript e pela comunicação eficiente por meio de APIs Web.

O ASP.NET Core é otimizado para aplicativos Web modernos e cenários de hospedagem baseada em nuvem. Seu design modular permite que os aplicativos dependam somente dos recursos que realmente usarem, melhorando o desempenho e a segurança do aplicativo e, ao mesmo tempo, reduzindo os requisitos de recursos de hospedagem.

## <a name="reference-application-eshoponweb"></a>Referência de aplicativo: eShopOnWeb

Estas diretrizes incluem um aplicativo de referência, o _eShopOnWeb_, que demonstra alguns dos princípios e das recomendações. O aplicativo é uma loja online simples compatível com navegação em um catálogo de camisetas, canecas e outros itens de marketing. O aplicativo de referência é deliberadamente simples para facilitar o entendimento.

![eShopOnWeb](./media/image2-1.png)

**Figura 2-1.** eShopOnWeb

> ### <a name="reference-application"></a>Aplicativo de referência
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>Hospedado na nuvem e escalonável

O ASP.NET Core é otimizado para a nuvem (nuvem pública, nuvem privada, qualquer nuvem) porque tem baixa memória e alta taxa de transferência. Uma superfície menor dos aplicativos ASP.NET Core significa que você pode hospedar mais partes dele no mesmo hardware e pagar por menos recursos quando usar os serviços pré-pagos de hospedagem na nuvem. A taxa de transferência mais alta significa que você pode atender mais clientes por meio de um aplicativo considerando o mesmo hardware, reduzindo ainda mais a necessidade de investir em servidores e na infraestrutura de hospedagem.

## <a name="cross-platform"></a>Plataforma cruzada

O ASP.NET Core é multiplataforma e pode ser executado no Windows, no macOS e no Linux. Isso proporciona muitas novas opções para o desenvolvimento e a implantação de aplicativos criados com o ASP.NET Core. Os contêineres do Docker, tanto do Linux quanto do Windows, podem hospedar aplicativos ASP.NET Core, permitindo que eles aproveitem os benefícios de [contêineres e microsserviços](../microservices/index.md).

## <a name="modular-and-loosely-coupled"></a>Flexível e acoplado de forma flexível

Os pacotes NuGet são cidadãos de primeira classe no .NET Core, e os aplicativos ASP.NET Core são compostos por muitas bibliotecas por meio do NuGet. Essa granularidade da funcionalidade ajuda a garantir que os aplicativos dependam e implantem somente a funcionalidade de que realmente precisam, reduzindo sua área da superfície de vulnerabilidade de segurança.

ASP.NET Core também suporta totalmente [a injeção de dependência,](https://deviq.com/dependency-injection/)tanto internamente quanto no nível de aplicação. As interfaces podem ter várias implementações que podem ser alternadas, conforme necessário. A injeção de dependência permite que os aplicativos sejam acoplados de modo flexível a essas interfaces, em vez de a implementações específicas, facilitando a extensão, a manutenção e o teste.

## <a name="easily-tested-with-automated-tests"></a>Testados facilmente com testes automatizados

Os aplicativos ASP.NET Core são compatíveis com teste de unidade, além disso, o acoplamento flexível e o suporte a injeções de dependência facilitam a alternância de interesses da infraestrutura com implementações fictícias para fins de teste. ASP.NET Core também é fornecido com um TestServer que pode ser usado para hospedar aplicativos na memória. Os testes funcionais podem então fazer solicitações para esse servidor em memória, exercitando a pilha completa do aplicativo (incluindo middleware, roteamento, model binding, filtros, etc.) e recebendo uma resposta, tudo isso em uma fração do tempo que levaria para hospedar o aplicativo em um servidor real e fazer solicitações por meio da camada de rede. Esses testes são especialmente fáceis de serem gravados e significativos para APIs, que são cada vez mais importantes em aplicativos Web modernos.

## <a name="traditional-and-spa-behaviors-supported"></a>Comportamentos tradicionais e de SPA com suporte

Os aplicativos Web tradicionais envolvem pouco comportamento do lado do cliente e, em vez disso, dependem do servidor para todas as consultas, atualizações e navegação que o aplicativo pode precisar fazer. Cada nova operação feita pelo usuário é convertida em uma nova solicitação da Web, com o resultado sendo um recarregamento de página inteira no navegador do usuário final. As estruturas MVC (Modelo-Exibição-Controlador) clássicas normalmente seguem essa abordagem, com cada nova solicitação correspondente a uma ação de controlador diferente, que, por sua vez, trabalham com um modelo e retornam uma exibição. Algumas operações individuais em determinada página podem ser aprimoradas com a funcionalidade AJAX (Asynchronous JavaScript And XML), mas a arquitetura geral do aplicativo usava muitas diferentes exibições do MVC e pontos de extremidade de URL. Além disso, o ASP.NET Core MVC também é compatível com Razor Pages, uma maneira mais simples para organizar as páginas de estilo MVC.

Por outro lado, os SPAs (aplicativos de página única) envolvem muito poucos carregamentos de página do lado do servidor gerados dinamicamente (se houver). Muitos SPAs são inicializados em um arquivo HTML estático que carrega as bibliotecas JavaScript necessárias para iniciar e executar o aplicativo. Esses aplicativos fazem uso intenso de APIs Web para suas necessidades de dados e podem fornecer experiências do usuário muito mais avançadas.

Muitos aplicativos Web envolvem uma combinação do comportamento do aplicativo Web tradicional (normalmente para o conteúdo) e SPAs (para a interatividade). O ASP.NET Core é compatível com o MVC (baseado em Exibições ou em Páginas) e com as APIs Web no mesmo aplicativo, usando o mesmo conjunto de ferramentas e de bibliotecas da estrutura subjacentes.

## <a name="simple-development-and-deployment"></a>Desenvolvimento e implantação simples

ASP.NET aplicativos Core podem ser escritos usando editores de texto simples e interfaces de linha de comando, ou ambientes de desenvolvimento completos, como o Visual Studio. Normalmente, os aplicativos monolíticos são implantados em um único ponto de extremidade. As implantações podem ser automatizadas com facilidade para ocorrerem como parte de um pipeline de CI (integração contínua) e CD (entrega contínua). Além das ferramentas tradicionais de CI/CD, o Microsoft Azure tem suporte integrado para repositórios git e pode implantar automaticamente atualizações à medida que são feitas em uma filial ou tag especificada. O Azure DevOps fornece um pipeline completo de construção e implantação de CI/CD, e o GitHub Actions fornece outra opção para projetos hospedados lá.

## <a name="traditional-aspnet-and-web-forms"></a>ASP.NET tradicional e Web Forms

Além do ASP.NET Core, o ASP.NET 4.x tradicional continua sendo uma plataforma robusta e confiável para a criação de aplicativos Web. ASP.NET suporta modelos de desenvolvimento de MVC e API web, bem como Formulários Web, que é adequado para o rico desenvolvimento de aplicativos baseados em páginas e apresenta um rico ecossistema de componentes de terceiros. O Microsoft Azure tem um ótimo suporte de longa data para ASP.NET aplicativos 4.x, e muitos desenvolvedores estão familiarizados com essa plataforma.

## <a name="blazor"></a>Blazor

Blazor está incluído com ASP.NET Core 3.0 e posterior. Ele fornece um novo mecanismo para criar aplicativos de clientes web interativos ricos usando Razor, C#e ASP.NET Core. Ele oferece outra solução a considerar ao desenvolver aplicações web modernas. Há duas versões do Blazor a considerar: lado do servidor e lado do cliente.

O lado do servidor Blazor foi lançado em 2019 com ASP.NET Core 3.0. Como o nome indica, ele é executado no servidor, renderizando alterações no documento do cliente de volta para o navegador pela rede. O Lado do servidor Blazor oferece uma experiência de cliente rica sem exigir JavaScript do lado do cliente e sem exigir cargas de página separadas para cada interação de página do cliente. As alterações na página carregada são solicitadas e processadas pelo servidor e, em seguida, enviadas de volta ao cliente usando signalR.

O Lado cliente Blazor será lançado em 2020 e eliminará a necessidade de renderizar alterações no servidor. Em vez disso, ele aproveitará o WebAssembly para executar o código .NET dentro do cliente. O cliente ainda pode fazer chamadas de API para o servidor se necessário para solicitar dados, mas todo o comportamento do lado do cliente é executado no cliente via WebAssembly, que já é suportado por todos os principais navegadores e é apenas uma biblioteca Javascript.

> ### <a name="references--modern-web-applications"></a>Referências – Aplicativos Web modernos
>
> - **Introdução ao ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **Teste no ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - **Blazor - Comece**  
>   <https://blazor.net/docs/get-started.html>

>[!div class="step-by-step"]
>[Próximo](index.md)
>[anterior](choose-between-traditional-web-and-single-page-apps.md)
