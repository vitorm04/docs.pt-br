---
title: Comparação de arquitetura de ASP.NET Web Forms e mais incrivelmente
description: Saiba como as arquiteturas do ASP.NET Web Forms e do mais claro comparações.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 8ff733178e684666b69859bfab8b79fbad1fdff6
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520314"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-blazor"></a>Comparação de arquitetura de ASP.NET Web Forms e mais incrivelmente

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Embora o ASP.NET Web Forms e o mais bem tenham muitos conceitos semelhantes, há diferenças em como eles funcionam. Este capítulo examina os trabalhos internos e as arquiteturas de ASP.NET Web Forms e mais úteis.

## <a name="aspnet-web-forms"></a>Web Forms do ASP.NET

O ASP.NET Web Forms Framework se baseia em uma arquitetura centrada em página. Cada solicitação HTTP para um local no aplicativo é uma página separada com a qual o ASP.NET responde. À medida que as páginas são solicitadas, o conteúdo do navegador é substituído pelos resultados da página solicitada.

As páginas consistem nos seguintes componentes:

- Marcação HTML
- Código em C# ou Visual Basic
- Uma classe code-behind que contém recursos de lógica e manipulação de eventos
- Controles

Os controles são unidades reutilizáveis da interface do usuário da Web que podem ser colocadas e interagir de forma programática em uma página. As páginas são compostas por arquivos que terminam com *. aspx* contendo marcação, controles e algum código. As classes code-behind estão em arquivos com o mesmo nome base e uma extensão *. aspx.cs* ou *. aspx. vb* , dependendo da linguagem de programação usada. Curiosamente, o servidor Web interpreta o conteúdo dos arquivos *. aspx* e os compila sempre que eles forem alterados. Essa recompilação ocorre mesmo que o servidor Web já esteja em execução.

Os controles podem ser criados com marcação e entregues como controles de usuário. Um controle de usuário deriva da classe `UserControl` e tem uma estrutura semelhante à página. A marcação para controles de usuário é armazenada em um arquivo *. ascx* . Uma classe code-behind acompanhante reside em um arquivo *. ascx.cs* ou *. ascx. vb* . Os controles também podem ser compilados completamente com o código, herdando da classe base `WebControl` ou `CompositeControl`.

As páginas também têm um ciclo de vida de eventos extensivo. Cada página gera eventos para os eventos de inicialização, carregamento, PreRender e Unload que ocorrem quando o tempo de execução ASP.NET executa o código da página para cada solicitação.

Os controles em uma página normalmente são postbacks para a mesma página que apresentou o controle e transportam-se por uma carga de um campo de formulário oculto chamado `ViewState`. O campo `ViewState` contém informações sobre o estado dos controles no momento em que eles foram renderizados e apresentados na página, permitindo que o tempo de execução do ASP.NET compare e identifique alterações no conteúdo enviado ao servidor.

## <a name="blazor"></a>Blazor

O mais alto é uma estrutura de interface do usuário da Web do lado do cliente semelhante à natureza das estruturas de front-end do JavaScript como angular ou reagir. O mais bem lida com as interações do usuário e renderiza as atualizações necessárias da interface do usuário. O mais alto *não* se baseia em um modelo de solicitação-resposta. As interações do usuário são tratadas como eventos que não estão no contexto de nenhuma solicitação HTTP específica.

Os aplicativos mais incrivelmente consistem em um ou mais componentes raiz que são processados em uma página HTML.

![Componentes mais incrivelmente em HTML](./media/architecture-comparison/blazor-components-in-html.png)

Como o usuário especifica onde os componentes devem renderizar e como os componentes são conectados para interações de usuário é o [modelo de hospedagem](hosting-models.md) específico.

Os [componentes](components.md) mais úteis são classes .NET que representam uma parte reutilizável da interface do usuário. Cada componente mantém seu próprio Estado e especifica sua própria lógica de renderização, que pode incluir a renderização de outros componentes. Os componentes especificam manipuladores de eventos para interações específicas do usuário para atualizar o estado do componente.

Depois que um componente manipula um evento, o mais incrivelmente processa o componente e controla o que mudou na saída renderizada. Os componentes não são renderizados diretamente para o Modelo de Objeto do Documento (DOM). Em vez disso, eles são renderizados em uma representação na memória do DOM chamado de `RenderTree` para que o mais claro possa rastrear as alterações. O mais eficiente compara a saída processada recentemente com a saída anterior para calcular uma comparação de interface do usuário que ela aplica com eficiência ao DOM.

![Interação do DOM do mais incrivelmente](./media/architecture-comparison/blazor-dom-interaction.png)

Os componentes também podem indicar manualmente que devem ser renderizados se seu estado for alterado fora de um evento de interface do usuário normal. O mais alto uso de um `SynchronizationContext` para impor um único thread lógico de execução. Os métodos de ciclo de vida de um componente e quaisquer retornos de chamada de evento que são gerados pelo mais alto são executados nesse `SynchronizationContext`.

>[!div class="step-by-step"]
>[Anterior](introduction.md)
>[Próximo](hosting-models.md)
