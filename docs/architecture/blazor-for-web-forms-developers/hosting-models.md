---
title: Modelos de Hospedagem de aplicativos mais incrivelmente
description: Conheça as diferentes maneiras de hospedar um aplicativo mais novo, incluindo no navegador no Webassembly ou no servidor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 5bf55fa686691acc25508d3d9a6dfaf8aca321ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088051"
---
# <a name="blazor-app-hosting-models"></a>Modelos de Hospedagem de aplicativos mais incrivelmente

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Os aplicativos mais simples podem ser hospedados no IIS, assim como ASP.NET Web Forms aplicativos. Os aplicativos mais incrivelmenteos também podem ser hospedados de uma das seguintes maneiras:

- No lado do cliente no navegador no Webassembly.
- No lado do servidor em um aplicativo ASP.NET Core.

## <a name="blazor-webassembly-apps"></a>Aplicativos Webassembly mais incrivelmente

Os aplicativos Webassembly mais incrivelmente executados diretamente no navegador em um tempo de execução .NET baseado em Webassembly. Os aplicativos Webassembly mais avançados funcionam de forma semelhante às estruturas JavaScript de front-end como angular ou reagir. No entanto, em vez de escrever C#o JavaScript que você escreve. O tempo de execução do .NET é baixado com o aplicativo junto com o assembly do aplicativo e as dependências necessárias. Não são necessários plug-ins ou extensões de navegador.

Os assemblies baixados são assemblies normais do .NET, como você usaria em qualquer outro aplicativo .NET. Como o tempo de execução dá suporte a .NET Standard, você pode usar bibliotecas de .NET Standard existentes com seu aplicativo Webassembly mais incrivelmente. No entanto, esses assemblies ainda serão executados na área restrita de segurança do navegador. Algumas funcionalidades podem gerar uma <xref:System.PlatformNotSupportedException>, como tentar acessar o sistema de arquivos ou abrir conexões de rede arbitrárias.

Quando o aplicativo é carregado, o tempo de execução do .NET é iniciado e apontado para o assembly do aplicativo. A lógica de inicialização do aplicativo é executada e os componentes raiz são renderizados. O mais incrivelmente calcula as atualizações da interface do usuário com base na saída renderizada dos componentes. As atualizações do DOM são aplicadas.

![WebAssembly Blazor](media/hosting-models/blazor-webassembly.png)

Aplicativos Webassembly de mais alto do que executam exclusivamente o lado do cliente. Esses aplicativos podem ser implantados em soluções de Hospedagem de site estáticos, como páginas do GitHub ou Hospedagem de sites estáticos do Azure. O .NET não é necessário no servidor. A vinculação profunda com partes do aplicativo normalmente requer uma solução de roteamento no servidor. A solução de roteamento redireciona as solicitações para a raiz do aplicativo. Por exemplo, esse redirecionamento pode ser tratado usando regras de reescrita de URL no IIS.

Para obter todos os benefícios de um desenvolvimento para a Web completo e de pilha completa, hospede seu aplicativo Webassembly mais novo com ASP.NET Core. Usando o .NET no cliente e no servidor, você pode compartilhar facilmente o código e criar seu aplicativo usando um conjunto consistente de linguagens, estruturas e ferramentas. O mais novo fornece modelos convenientes para configurar uma solução que contenha um aplicativo Webassembly mais novo e um projeto de host ASP.NET Core. Quando a solução é criada, os arquivos estáticos internos do aplicativo mais elaborado são hospedados pelo aplicativo ASP.NET Core com o roteamento de fallback já configurado.

## <a name="blazor-server-apps"></a>Aplicativos de servidor mais incrivelmenteos

Lembre-se da discussão de [arquitetura mais incrivelmente](architecture-comparison.md#blazor) que os componentes mais flexíveis renderizam a saída para uma abstração intermediária chamada de `RenderTree`. A estrutura mais incrivelmente compara o que foi renderizado com o que foi renderizado anteriormente. As diferenças são aplicadas ao DOM. Os componentes mais flexíveis são dissociados de como a saída renderizada é aplicada. Consequentemente, os próprios componentes não precisam ser executados no mesmo processo que o processo que atualiza a interface do usuário. Na verdade, eles nem precisam ser executados no mesmo computador.

Em aplicativos de servidor mais incrivelmente, os componentes são executados no servidor, em vez de no lado do cliente no navegador. Os eventos de interface do usuário que ocorrem no navegador são enviados para o servidor em uma conexão em tempo real. Os eventos são expedidos para as instâncias de componente corretas. Os componentes são renderizados e a comparação de interface do usuário calculada é serializada e enviada ao navegador onde é aplicada ao DOM.

![Servidor Blazor](media/hosting-models/blazor-server.png)

O modelo de Hospedagem de servidor mais robusto pode parecer familiar se você tiver usado o ASP.NET AJAX e o controle de <xref:System.Web.UI.UpdatePanel>. O controle de `UpdatePanel` lida com a aplicação de atualizações parciais de página em resposta a eventos de gatilho na página. Quando disparado, o `UpdatePanel` solicita uma atualização parcial e, em seguida, a aplica sem a necessidade de atualizar a página. O estado da interface do usuário é gerenciado usando `ViewState`. Os aplicativos de servidor mais poseriais são um pouco diferentes em que o aplicativo requer uma conexão ativa com o cliente. Além disso, todo o estado da interface do usuário é mantido no servidor. Além dessas diferenças, os dois modelos são conceitualmente semelhantes.

## <a name="how-to-choose-the-right-blazor-hosting-model"></a>Como escolher o modelo de hospedagem mais adequado

Conforme descrito nos [documentos de modelo de hospedagem](https://docs.microsoft.com/aspnet/core/blazor/hosting-models#server-side)mais bem, os diferentes modelos de Hospedagem de mais e-ou outros têm compensações diferentes.

O modelo de hospedagem Webassembly mais incrivelmente tem os seguintes benefícios:

- Não há nenhuma dependência do lado do servidor .NET. O aplicativo está totalmente funcionando depois de baixado para o cliente.
- Recursos e funcionalidades do cliente são totalmente aproveitados.
- O trabalho é descarregado do servidor para o cliente.
- Um servidor Web ASP.NET Core não é necessário para hospedar o aplicativo. Cenários de implantação sem servidor são possíveis (por exemplo, servindo o aplicativo de uma CDN).

As desvantagens do modelo de hospedagem Webassembly mais incrivelmente são:

- Os recursos do navegador restringem o aplicativo.
- Hardware e software de cliente com capacidade (por exemplo, suporte a Webassembly) é necessário.
- O tamanho do download é maior e os aplicativos demoram mais para serem carregados.
- O suporte ao tempo de execução e às ferramentas do .NET é menos maduro. Por exemplo, há limitações no suporte e na depuração de [.net Standard](../../standard/net-standard.md) .

Por outro lado, o modelo de Hospedagem de servidor mais incrivelmente oferece os seguintes benefícios:

- O tamanho do download é muito menor do que um aplicativo do lado do cliente e o aplicativo é carregado muito mais rapidamente.
- O aplicativo aproveita totalmente os recursos do servidor, incluindo o uso de qualquer API compatível com o .NET Core.
- O .NET Core no servidor é usado para executar o aplicativo, portanto, as ferramentas .NET existentes, como depuração, funcionam conforme o esperado.
- Há suporte para clientes finos. Por exemplo, aplicativos do lado do servidor funcionam com navegadores que não dão suporte ao Webassembly e a dispositivos com restrição de recursos.
- A base .NET/C# código do aplicativo, incluindo o código de componente do aplicativo, não é servida aos clientes.

As desvantagens do modelo de Hospedagem de servidor mais incrivelmente são:

- Maior latência de interface do usuário. Cada interação do usuário envolve um salto de rede.
- Não há suporte offline. Se a conexão do cliente falhar, o aplicativo para de funcionar.
- A escalabilidade é desafiadora para aplicativos com muitos usuários. O servidor deve gerenciar várias conexões de cliente e manipular o estado do cliente.
- Um servidor de ASP.NET Core é necessário para atender ao aplicativo. Cenários de implantação sem servidor não são possíveis. Por exemplo, você não pode servir o aplicativo de uma CDN.

A lista anterior de compensações pode ser intimidadora, mas seu modelo de hospedagem pode ser alterado posteriormente. Independentemente do modelo de hospedagem mais incrivelmente selecionado, o modelo de componente é *o mesmo*. Em princípio, os mesmos componentes podem ser usados com o modelo de hospedagem. O código do aplicativo não é alterado; no entanto, é uma boa prática introduzir abstrações para que seus componentes fiquem de hospedagem independente de modelo. As abstrações permitem que seu aplicativo adote com mais facilidade um modelo de hospedagem diferente.

## <a name="deploy-your-app"></a>Implantar seu aplicativo

Os aplicativos de Web Forms ASP.NET normalmente são hospedados no IIS em um computador ou cluster do Windows Server. Aplicativos mais incrivelmenteos também podem:

- Ser hospedado no IIS, seja como arquivos estáticos ou como um aplicativo ASP.NET Core.
- Aproveite a flexibilidade de ASP.NET Core para ser hospedada em várias plataformas e infraestruturas de servidor. Por exemplo, você pode hospedar um aplicativo mais novo usando [Nginx](/aspnet/core/host-and-deploy/linux-nginx) ou [Apache](/aspnet/core/host-and-deploy/linux-apache) no Linux. Para obter mais informações sobre como publicar e implantar aplicativos mais podestas, consulte a documentação de [hospedagem e implantação](/aspnet/core/host-and-deploy/blazor/) mais incrivelmente.

Na próxima seção, veremos como os projetos para Webassembly e aplicativos de servidor mais poredondadores são configurados.

>[!div class="step-by-step"]
>[Anterior](architecture-comparison.md)
>[Próximo](project-structure.md)
