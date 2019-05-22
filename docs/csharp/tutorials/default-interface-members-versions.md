---
title: Atualizar interfaces com segurança usando membros de interface padrão em C#
description: Este tutorial avançado explora como adicionar novos recursos com segurança às definições de interface existentes sem interromper todas as classes e structs que implementam essa interface.
ms.date: 05/06/2019
ms.custom: mvc
ms.openlocfilehash: 2daa40ead5902454c6d45390233e1491fe6d369b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877910"
---
# <a name="tutorial-update-interfaces-with-default-interface-members-in-c-80"></a>Tutorial: Atualizar interfaces com membros da interface padrão no C# 8.0

Desde o C# 8.0 no .NET Core 3.0, é possível definir uma implementação em que você declara um membro de uma interface. O cenário mais comum é adicionar membros com segurança a uma interface já lançada e usada por vários clientes.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Estender interfaces com segurança, adicionando métodos com implementações.
> * Criar implementações parametrizadas para oferecer maior flexibilidade.
> * Permitir que os implementadores forneçam uma implementação mais específica na forma de uma substituição.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar o computador para executar o .NET Core, incluindo o compilador da versão prévia do C# 8.0. O compilador da versão prévia do C# 8.0 está disponível no [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou no [SDK de versão prévia do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0) mais recente. Membros de interface padrão estão disponíveis desde a versão prévia 4 do .NET Core 3.0.

## <a name="scenario-overview"></a>Visão geral do cenário

Este tutorial começa com a versão 1 de uma biblioteca de relacionamento com o cliente. Você pode obter o aplicativo de iniciante em nosso [repositório de exemplos no GitHub](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/starter/customer-relationship). A empresa que criou essa biblioteca pretendia que clientes com aplicativos existentes adotassem a biblioteca. Eles forneciam definições de interface mínimas para os usuários da biblioteca implementarem. Aqui está a definição de interface para um cliente:

[!code-csharp[InitialCustomerInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/ICustomer.cs?name=SnippetICustomerVersion1)]

Eles definiram uma segunda interface que representava um pedido:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/starter/customer-relationship/IOrder.cs?name=SnippetIorderVersion1)]

Dessas interfaces, a equipe poderia criar uma biblioteca para os usuários criarem uma experiência melhor para os clientes. A meta era criar um relacionamento mais profundo com os clientes existentes e melhorar o relacionamento com clientes novos.

Agora é hora de atualizar a biblioteca para a próxima versão. Um dos recursos solicitados habilitará um desconto de fidelidade para os clientes que tiverem muitos pedidos. Esse novo desconto de fidelidade é aplicado sempre que um cliente faz um pedido. O desconto específico é uma propriedade de cada cliente. Cada implementação de ICustomer pode definir regras diferentes para o desconto de fidelidade. 

A forma mais natural de adicionar essa funcionalidade é melhorar a interface `ICustomer` com um método para aplicar qualquer desconto de fidelidade. Essa sugestão de design causou preocupação entre desenvolvedores experientes: "Interfaces são imutáveis depois que são lançadas! Esta é uma alteração da falha!" O C# 8.0 adiciona *implementações de interface padrão* para interfaces de atualização. Os autores de biblioteca podem adicionar novos membros à interface e fornecer uma implementação padrão para esses membros.

Implementações de interface padrão permitem que os desenvolvedores atualizem uma interface, permitindo que qualquer implementador substitua essa implementação. Os usuários da biblioteca podem aceitar a implementação padrão como uma alteração da falha. Se as regras de negócio forem diferentes, elas poderão substituir a implementação.

## <a name="upgrade-with-default-interface-members"></a>Atualizar com membros de interface padrão

A equipe concordou na implementação padrão mais provável: um desconto de fidelidade para os clientes.

A atualização deve fornecer a funcionalidade para definir duas propriedades: o número de pedidos necessários para ser qualificado para o desconto e o percentual de desconto. Isso se constitui em um cenário perfeito para membros de interface padrão. Você pode adicionar um método à interface ICustomer e fornecer a implementação mais provável. Todas as implementações novas e existentes podem usar a implementação padrão ou fornecer as suas próprias.

Primeiro, adicione o novo método à implementação:

[!code-csharp[InitialOrderInterface](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionOne)]

O autor da biblioteca escreveu um primeiro teste para verificar a implementação:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetTestDefaultImplementation)]

Observe a seguinte parte do teste:

[!code-csharp[TestDefaultImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetHighlightCast)]

Essa conversão de `SampleCustomer` em `ICustomer` é necessária. A classe `SampleCustomer` não precisa fornecer uma implementação de `ComputeLoyaltyDiscount`; isso é fornecido pela interface `ICustomer`. No entanto, a classe `SampleCustomer` não herda membros de suas interfaces. Essa regra não foi alterada. Para chamar qualquer método declarado e implementado na interface, a variável deve ser o tipo da interface: `ICustomer` neste exemplo.

## <a name="provide-parameterization"></a>Fornecer parametrização

Esse é um bom início. Porém, a implementação padrão é restritiva demais. Muitos consumidores desse sistema podem escolher limites diferentes para o número de compras, um período diferente de associação ou um percentual de desconto diferente. Você pode fornecer uma experiência de atualização melhor para mais clientes, fornecendo uma maneira de definir esses parâmetros. Vamos adicionar um método estático que defina esses três parâmetros, controlando a implementação padrão:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetLoyaltyDiscountVersionTwo)]

Há vários recursos novos de linguagem mostrados nesse pequeno fragmento de código. Agora as interfaces podem incluir membros estáticos, incluindo campos e métodos. Modificadores de acesso diferentes também estão habilitados. Os campos adicionais são particulares, o novo método é público. Qualquer dos modificadores são permitidos em membros de interface.

Aplicativos que usam a fórmula geral para calcular o desconto de fidelidade, mas que usam parâmetros diferentes, não precisam fornecer uma implementação personalizada; eles podem definir os argumentos por meio de um método estático. Por exemplo, o código a seguir define um "agradecimento ao cliente" que recompensa qualquer cliente com mais de um mês de associação:

[!code-csharp[SetLoyaltyThresholds](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/Program.cs?name=SnippetSetLoyaltyThresholds)]

## <a name="extend-the-default-implementation"></a>Estender a implementação padrão

O código que você adicionou até agora forneceu uma implementação conveniente para esses cenários em que os usuários querem algo semelhante à implementação padrão ou para fornecer um conjunto de regras não relacionado. Como um último recurso, vamos refatorar o código um pouco para permitir cenários em que os usuários queiram criar com base na implementação padrão. 

Considere uma startup que deseja atrair novos clientes. Eles oferecem um desconto de 50% no primeiro pedido de um novo cliente. Por outro lado, clientes existentes obtém o desconto padrão. O autor da biblioteca precisa mover a implementação padrão para um método `protected static`, de modo que qualquer classe que implemente essa interface possa reutilizar o código em sua implementação. A implementação padrão do membro da interface também chama esse método compartilhado:

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/ICustomer.cs?name=SnippetFinalVersion)]

Em uma implementação de uma classe que implementa essa interface, a substituição pode chamar o método auxiliar estático e estender essa lógica para fornecer o desconto de "novo cliente":

[!code-csharp[VersionTwoImplementation](~/samples/csharp/tutorials/default-interface-members-versions/finished/customer-relationship/SampleCustomer.cs?name=SnippetOverrideAndExtend)]

Você pode ver todo o código concluído em nosso [repositório de exemplos no GitHub] (Você pode obter o aplicativo de iniciante em nosso [repositório de exemplos no GitHub)](https://github.com/dotnet/samples/tree/master/csharp/tutorials/default-interface-members-versions/finished/customer-relationship).

Esses novos recursos significam que interfaces podem ser atualizadas com segurança quando há uma implementação padrão razoável para os novos membros. Projete interfaces cuidadosamente para expressar ideias funcionais únicas que possam ser implementadas por várias classes. Isso torna mais fácil atualizar essas definições de interface quando são descobertos novos requisitos para a mesma ideia funcional.
