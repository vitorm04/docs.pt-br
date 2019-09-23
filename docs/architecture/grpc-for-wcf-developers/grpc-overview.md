---
title: Visão geral do gRPC-gRPC para desenvolvedores do WCF
description: Saiba mais sobre o conjunto de princípios que orienta o desenvolvimento do gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: b372cc9dcdb2efd605b3d9b688513e4ff8530b01
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184438"
---
# <a name="grpc-overview"></a><span data-ttu-id="9b306-103">Visão geral do gRPC</span><span class="sxs-lookup"><span data-stu-id="9b306-103">gRPC overview</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9b306-104">Depois de examinar o Genesis do WCF e do gRPC no último capítulo, este capítulo considerará alguns dos principais recursos do gRPC e como eles se comparam ao WCF.</span><span class="sxs-lookup"><span data-stu-id="9b306-104">After looking at the genesis of both WCF and gRPC in the last chapter, this chapter will consider some of the key features of gRPC and how they compare to WCF.</span></span>

<span data-ttu-id="9b306-105">ASP.NET Core 3,0 é a primeira versão do ASP.NET que dá suporte nativamente ao gRPC como cidadão de primeira classe, com as equipes da Microsoft contribuindo para a implementação oficial do .NET do gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b306-105">ASP.NET Core 3.0 is the first release of ASP.NET that natively supports gRPC as a first-class citizen, with Microsoft teams contributing to the official .NET implementation of gRPC.</span></span> <span data-ttu-id="9b306-106">É recomendável como a melhor abordagem para a criação de aplicativos distribuídos com o .NET que podem interoperar com todas as outras linguagens de programação e estruturas principais.</span><span class="sxs-lookup"><span data-stu-id="9b306-106">It's recommended as the best approach for building distributed applications with .NET that can interoperate with all other major programming languages and frameworks.</span></span>

## <a name="key-principles"></a><span data-ttu-id="9b306-107">Principais princípios</span><span class="sxs-lookup"><span data-stu-id="9b306-107">Key principles</span></span>

<span data-ttu-id="9b306-108">Como discutido no capítulo 1, o Google queria usar a introdução do HTTP/2 para retrabalhar Stubby, sua infraestrutura de RPC de uso geral interna.</span><span class="sxs-lookup"><span data-stu-id="9b306-108">As discussed in chapter 1, Google wanted to use the introduction of HTTP/2 to rework Stubby, its internal, general purpose RPC infrastructure.</span></span> <span data-ttu-id="9b306-109">Stubby, renomeado como gRPC, agora pode aproveitar a padronização e estender sua aplicabilidade à computação móvel, à nuvem e à Internet das Coisas.</span><span class="sxs-lookup"><span data-stu-id="9b306-109">Stubby, renamed gRPC, now could take advantage of standardization and would extend its applicability to mobile computing, the cloud, and the Internet of Things.</span></span>

<span data-ttu-id="9b306-110">Para conseguir isso, a [CNCF (nuvem Native Computing Foundation)](https://www.cncf.io/) estabeleceu um conjunto de princípios que regeria o gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b306-110">To achieve this, the [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) established a set of principles that would govern gRPC.</span></span> <span data-ttu-id="9b306-111">A lista a seguir mostra as mais relevantes, que se preocupam principalmente com a maximização da acessibilidade e usabilidade:</span><span class="sxs-lookup"><span data-stu-id="9b306-111">The following list shows the most relevant ones, which are mainly concerned with maximizing accessibility and usability:</span></span>

- <span data-ttu-id="9b306-112">**Gratuito e aberto** – todos os artefatos devem ser de código aberto com licenciamento que não restrinja os desenvolvedores de adotar o gRPC.</span><span class="sxs-lookup"><span data-stu-id="9b306-112">**Free and open** – all artifacts should be open source with licensing that doesn't constrain developers from adopting gRPC.</span></span>
- <span data-ttu-id="9b306-113">**Cobertura e simplicidade** – o gRPC deve estar disponível em todas as plataformas populares e simples o suficiente para criar em qualquer plataforma.</span><span class="sxs-lookup"><span data-stu-id="9b306-113">**Coverage and simplicity** – gRPC should be available across every popular platform and simple enough to build on any platform.</span></span>
- <span data-ttu-id="9b306-114">**Interoperabilidade e alcance** – deve ser possível usar o gRPC em qualquer rede, independentemente da largura de banda ou da latência, usando padrões de rede amplamente disponíveis.</span><span class="sxs-lookup"><span data-stu-id="9b306-114">**Interoperability and reach** – it should be possible to use gRPC on any network, regardless of bandwidth or latency, using widely available network standards.</span></span>
- <span data-ttu-id="9b306-115">**Uso geral e desempenho** – a estrutura deve ser utilizável por uma ampla gama de casos de uso possível, sem comprometer o desempenho.</span><span class="sxs-lookup"><span data-stu-id="9b306-115">**General purpose and performant** – the framework should be usable by as broad a range of use-cases as possible without compromising performance.</span></span>
- <span data-ttu-id="9b306-116">**Streaming** – o protocolo deve fornecer semântica de streaming para grandes conjuntos de dados ou mensagens assíncronas.</span><span class="sxs-lookup"><span data-stu-id="9b306-116">**Streaming** – the protocol should provide streaming semantics for large data-sets or asynchronous messaging.</span></span>
- <span data-ttu-id="9b306-117">**Troca de metadados** – o protocolo permite que dados não comerciais, como tokens de autenticação, sejam tratados separadamente dos dados corporativos reais.</span><span class="sxs-lookup"><span data-stu-id="9b306-117">**Metadata exchange** – the protocol allow non-business data, such as authentication tokens, to be handled separately from actual business data.</span></span>
- <span data-ttu-id="9b306-118">**Códigos de status padronizados** – a variabilidade dos códigos de erro deve ser reduzida para tornar as decisões de tratamento de erros mais claras e, em que o tratamento de erros mais avançado é necessário, um mecanismo deve ser fornecido para gerenciar isso na troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="9b306-118">**Standardized status codes** – the variability of error codes should be reduced to make error handling decisions clearer and, where additional richer error handling is required, a mechanism should be provided for managing this within the metadata exchange.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9b306-119">[Anterior](introduction.md)
>[Próximo](approach.md)</span><span class="sxs-lookup"><span data-stu-id="9b306-119">[Previous](introduction.md)
[Next](approach.md)</span></span>
