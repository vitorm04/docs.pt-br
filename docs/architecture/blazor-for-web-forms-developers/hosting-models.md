---
title: Modelos de hospedagem de aplicativos Blazor
description: Aprenda as diferentes maneiras de hospedar um aplicativo Blazor, inclusive no navegador no WebAssembly ou no servidor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 77a022b01efba01038790c9601ea03f315a28fdf
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607926"
---
# <a name="blazor-app-hosting-models"></a>Modelos de hospedagem de aplicativos Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Os aplicativos Blazor podem ser hospedados no IIS, assim como ASP.NET aplicativos Web Forms. Os aplicativos Blazor também podem ser hospedados de uma das seguintes maneiras:

- Lado do cliente no navegador no WebAssembly.
- Lado do servidor em um aplicativo ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>Aplicativos Blazor WebAssembly

Os aplicativos Blazor WebAssembly são executados diretamente no navegador em um tempo de execução .NET baseado no WebAssembly. Os aplicativos Blazor WebAssembly funcionam de forma semelhante às estruturas JavaScript front-end, como Angular ou React. No entanto, em vez de escrever JavaScript você escreve C#. O tempo de execução .NET é baixado com o aplicativo, juntamente com a montagem do aplicativo e quaisquer dependências necessárias. Não são necessários plugins ou extensões do navegador.

Os conjuntos baixados são conjuntos normais .NET, como você usaria em qualquer outro aplicativo .NET. Como o tempo de execução suporta o .NET Standard, você pode usar bibliotecas .NET Standard existentes com o aplicativo Blazor WebAssembly. No entanto, esses conjuntos ainda serão executados na caixa de areia de segurança do navegador. Algumas funcionalidades podem <xref:System.PlatformNotSupportedException>lançar um , como tentar acessar o sistema de arquivos ou abrir conexões arbitrárias de rede.

Quando o aplicativo é carregado, o tempo de execução .NET é iniciado e apontado para a montagem do aplicativo. A lógica de inicialização do aplicativo é executada e os componentes raiz são renderizados. Blazor calcula as atualizações da UI com base na saída renderizada dos componentes. As atualizações do DOM são então aplicadas.

![WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

Os aplicativos Blazor WebAssembly são executados puramente do lado do cliente. Esses aplicativos podem ser implantados em soluções estáticas de hospedagem de sites, como páginas do GitHub ou hospedagem de sites estáticos do Azure. .NET não é necessário no servidor. A ligação profunda a partes do aplicativo normalmente requer uma solução de roteamento no servidor. A solução de roteamento redireciona as solicitações para a raiz do aplicativo. Por exemplo, esse redirecionamento pode ser tratado usando regras de reescrita de URL no IIS.

Para obter todos os benefícios do Blazor e do desenvolvimento web .NET full-stack, hospede seu aplicativo Blazor WebAssembly com ASP.NET Core. Ao usar o .NET no cliente e no servidor, você pode facilmente compartilhar código e construir seu aplicativo usando um conjunto consistente de idiomas, frameworks e ferramentas. Blazor fornece modelos convenientes para configurar uma solução que contenha tanto um aplicativo Blazor WebAssembly quanto um projeto de host ASP.NET Core. Quando a solução é construída, os arquivos estáticos construídos do aplicativo Blazor são hospedados pelo aplicativo ASP.NET Core com roteamento de retorno já configurado.

## <a name="blazor-server-apps"></a>Aplicativos do Blazor Server

Lembre-se da discussão da [arquitetura Blazor](architecture-comparison.md#blazor) de que os componentes `RenderTree`Blazor tornam sua produção para uma abstração intermediária chamada . O quadro blazor então compara o que foi prestado com o que foi anteriormente prestado. As diferenças são aplicadas ao DOM. Os componentes Blazor são dissociados de como sua saída renderizada é aplicada. Consequentemente, os componentes em si não têm que ser executados no mesmo processo que o processo de atualização da ui. Na verdade, eles nem têm que correr na mesma máquina.

Nos aplicativos do Blazor Server, os componentes são executados no servidor em vez do lado do cliente no navegador. Os eventos de interface do usuário que ocorrem no navegador são enviados ao servidor por uma conexão em tempo real. Os eventos são enviados para as instâncias corretas do componente. Os componentes renderizam, e o diferencial de interface do usuário calculado é serializado e enviado para o navegador onde é aplicado ao DOM.

![Servidor Blazor](media/hosting-models/blazor-server.png)

O modelo de hospedagem do Blazor Server pode soar <xref:System.Web.UI.UpdatePanel> familiar se você usou ASP.NET AJAX e o controle. O `UpdatePanel` controle lida com a aplicação de atualizações parciais de página em resposta aos eventos de acionamento na página. Quando acionado, `UpdatePanel` o solicita uma atualização parcial e, em seguida, aplica-a sem precisar atualizar a página. O estado da ui é `ViewState`gerenciado usando . Os aplicativos Blazor Server são ligeiramente diferentes, na época em que o aplicativo requer uma conexão ativa com o cliente. Além disso, todo o estado de IU é mantido no servidor. Além dessas diferenças, os dois modelos são conceitualmente semelhantes.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Como escolher o modelo de hospedagem Blazor certo

Como descrito nos [docs do modelo de hospedagem Blazor, os diferentes modelos](/aspnet/core/blazor/hosting-models)de hospedagem Blazor têm diferentes trocas.

O modelo de hospedagem Blazor WebAssembly tem os seguintes benefícios:

- Não há dependência do lado do servidor .NET. O aplicativo está funcionando plenamente depois de baixado para o cliente.
- Os recursos e recursos do cliente são totalmente aproveitados.
- O trabalho é descarregado do servidor para o cliente.
- Um servidor web ASP.NET Core não é necessário para hospedar o aplicativo. Cenários de implantação sem servidor são possíveis (por exemplo, servindo o aplicativo a partir de um CDN).

As desvantagens do modelo de hospedagem Do Blazor WebAssembly são:

- Os recursos do navegador restringem o aplicativo.
- É necessário hardware e software de cliente capazes (por exemplo, suporte ao WebAssembly).
- O tamanho do download é maior e os aplicativos demoram mais para carregar.
- O tempo de execução .NET e o suporte a ferramentas são menos maduros. Por exemplo, há limitações no suporte e depuração [do .NET Standard.](../../standard/net-standard.md)

Por outro lado, o modelo de hospedagem do Blazor Server oferece os seguintes benefícios:

- O tamanho do download é muito menor do que um aplicativo do lado do cliente, e o aplicativo carrega muito mais rápido.
- O aplicativo aproveita ao máximo os recursos do servidor, incluindo o uso de quaisquer APIs compatíveis com o .NET Core.
- O .NET Core no servidor é usado para executar o aplicativo, então a ferramenta .NET existente, como a depuração, funciona como esperado.
- Clientes magros são suportados. Por exemplo, aplicativos do lado do servidor funcionam com navegadores que não suportam o WebAssembly e em dispositivos com restrição de recursos.
- A base de código .NET/C#do aplicativo, incluindo o código de componentes do aplicativo, não é servida aos clientes.

As desvantagens do modelo de hospedagem do Blazor Server são:

- Maior latência da UI. Toda interação do usuário envolve um salto de rede.
- Não há suporte offline. Se a conexão com o cliente falhar, o aplicativo pára de funcionar.
- A escalabilidade é um desafio para aplicativos com muitos usuários. O servidor deve gerenciar várias conexões com clientes e lidar com o estado do cliente.
- Um servidor ASP.NET Core é necessário para servir o aplicativo. Cenários de implantação sem servidor não são possíveis. Por exemplo, você não pode servir o aplicativo de um CDN.

A lista anterior de trade-offs pode ser intimidante, mas seu modelo de hospedagem pode ser alterado mais tarde. Independentemente do modelo de hospedagem Blazor selecionado, o modelo componente é *o mesmo*. Em princípio, os mesmos componentes podem ser usados com qualquer modelo de hospedagem. O código do aplicativo não muda; no entanto, é uma boa prática introduzir abstrações para que seus componentes permaneçam hospedando modelo-agnóstico. As abstrações permitem que seu aplicativo adote mais facilmente um modelo de hospedagem diferente.

## <a name="deploy-your-app"></a>Implantar seu aplicativo

ASP.NET aplicativos web forms são normalmente hospedados no IIS em uma máquina ou cluster do Windows Server. Os aplicativos Blazor também podem:

- Esteja hospedado no IIS, seja como arquivos estáticos ou como um aplicativo ASP.NET Core.
- Aproveite ASP.NET flexibilidade do Core seja hospedada em várias plataformas e infra-estruturas de servidores. Por exemplo, você pode hospedar um Aplicativo Blazor usando [Nginx](/aspnet/core/host-and-deploy/linux-nginx) ou [Apache](/aspnet/core/host-and-deploy/linux-apache) no Linux. Para obter mais informações sobre como publicar e implantar aplicativos Blazor, consulte a documentação [de hospedagem e implantação do](/aspnet/core/host-and-deploy/blazor/) Blazor.

Na próxima seção, veremos como os projetos para os aplicativos Blazor WebAssembly e Blazor Server são configurados.

>[!div class="step-by-step"]
>[Próximo](architecture-comparison.md)
>[anterior](project-structure.md)
