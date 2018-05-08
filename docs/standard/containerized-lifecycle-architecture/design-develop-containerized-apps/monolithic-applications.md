---
title: Aplicativos monolíticos
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: fe25fa8772c60625c5564d5e7194957366a6010a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="monolithic-applications"></a>Aplicativos monolíticos

Nesse cenário, você está criando um aplicativo da web simples e monolítico ou serviço e implantá-lo como um contêiner. Dentro do aplicativo, a estrutura pode não ser monolítica; ele pode abranger vários componentes, bibliotecas ou até mesmo camadas (camada de aplicativo, camada de domínio, camada de acesso a dados, etc.). Externamente, é um único contêiner, como um único processo, um único aplicativo web ou um único serviço.

Para gerenciar esse modelo, implante um contêiner único para representar o aplicativo. Para dimensioná-lo, basta Adicione algumas cópias mais com um balanceador de carga na frente. A simplicidade é proveniente do gerenciamento de uma única implantação em um único contêiner ou a máquina virtual (VM).

A entidade de segurança que um contêiner não apenas uma coisa e faz isso em um processo, a seguir o padrão monolítico está em conflito. Você pode incluir vários componentes/bibliotecas ou camadas internas dentro de cada contêiner, conforme ilustrado na Figura 4-1.

![](./media/image1.png)

Figura 4-1: um exemplo de arquitetura do aplicativo monolítico

A desvantagem dessa abordagem é fornecido se ou quando o aplicativo cresce, solicitá-la para dimensionar. Se o aplicativo inteiro for dimensionado, isso não será realmente um problema. No entanto, na maioria dos casos, algumas partes do aplicativo são os pontos de restrição que exigem o dimensionamento, enquanto que outros componentes são usados com menor.

Usando o exemplo de comércio eletrônico típico, você provavelmente precisa é de dimensionar o componente de informações do produto. Uma quantidade muito maior de clientes procura produtos em vez de comprá-los. Mais clientes usam o carrinho em vez do pipeline de pagamento. Menos clientes fazem comentários ou exibem o histórico de compras. E você provavelmente tem apenas uma série de funcionários, em uma única região, o que precisa para gerenciar o conteúdo e campanhas de marketing. Dimensionando o design monolítico, todo o código é implantado várias vezes.

Além de "escala-tudo" problema, alterações em um único componente exigem que o teste completo de todo o aplicativo, bem como uma reimplantação completa de todas as instâncias.

A abordagem monolítica é comum, e muitas organizações estão desenvolvendo com esse método de arquitetura. Muitos bom desfrutam resultados suficientes, enquanto outros encontram limites. Muitos criados seus aplicativos no modelo porque as ferramentas e infraestrutura foram muito difícil criar SOAs, e eles não verão a necessidade, até que o aplicativo aumentou.

De uma perspectiva de infraestrutura, cada servidor pode executar muitos aplicativos dentro do mesmo host e tiver uma taxa aceitável de eficiência em seu uso de recursos, como mostrado na Figura 4-2.

![](./media/image2.png)

Figura 4-2: um host executando vários aplicativos/contêineres

Você pode implantar aplicativos monolíticos no Azure usando VMs dedicadas para cada instância. Usando [conjuntos de escala de VM do Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), você pode dimensionar as VMs facilmente. Os [Serviços de Aplicativos do Azure](https://azure.microsoft.com/en-us/services/app-service/) podem executar aplicativos monolíticos e dimensionar instâncias com facilidade, sem a necessidade de gerenciar as VMs. Desde 2016, serviços de aplicativo do Azure pode executar instâncias únicas de contêineres do Docker, também, simplificando a implantação. E, usando o Docker, você pode implantar uma única VM como um host Docker e executar várias instâncias. Usando o balanceador do Azure, conforme ilustrado na Figura 4-3, você pode gerenciar a escala.

![](./media/image3.png)

Figura 4-3: vários hosts expansão um único aplicativo aplicativos/contêineres do Docker

Você pode gerenciar a implantação em vários hosts por meio de técnicas tradicionais de implantação. Você pode gerenciar os hosts de Docker usando comandos como `docker run` manualmente, por meio de automação, como os pipelines de entrega contínua (CD), que explicaremos mais tarde neste livro eletrônico.

## <a name="monolithic-application-deployed-as-a-container"></a>Aplicativo monolítico implantado como um contêiner

Há benefícios de usar contêineres para gerenciar implantações monolíticos. O dimensionamento das instâncias de contêineres é muito mais rápido e fácil do que a implantação de VMs adicionais. Embora os conjuntos de escala de VM são um ótimo recurso para dimensionar VMs, que são necessários para hospedar seus contêineres do Docker, eles têm tempo para configurar. Quando implantada como instâncias de aplicativo, a configuração do aplicativo é gerenciada como parte da VM.

Implantar atualizações como imagens do Docker é muito mais rápido e eficiente em termos de rede. As instâncias de Vn podem ser configuradas nos mesmos hosts que suas instâncias Vn-1, eliminando custos adicionais resultantes de VMs adicionais. Imagens do docker geralmente iniciam em segundos, acelerando distribuições. Subdividir uma instância de Docker é tão fácil quanto invocando o `docker stop` comando, normalmente Concluindo em menos de um segundo.

Como os contêineres são inerentemente imutáveis, por design, você nunca precisa se preocupar sobre VMs corrompidas porque esqueceu de um script de atualização de conta para alguma configuração específica ou o arquivo deixado no disco.

Embora monolíticos aplicativos podem se beneficiar do Docker, estejamos tocando em apenas as dicas de benefícios. Os maiores benefícios de gerenciar contêineres vem da implantação de orchestrators de contêiner que gerenciam a várias instâncias e ciclo de vida de cada instância de contêiner. Dividir o aplicativo monolítico em subsistemas que podem ser dimensionados, desenvolvidos e implantados individualmente é o ponto de entrada no universo dos microsserviços.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publicar um único aplicativo de contêiner do Docker do serviço de aplicativo do Azure

Ou porque você deseja obter uma validação rápida de um contêiner implantado no Azure ou porque o aplicativo é simplesmente um aplicativo único contêiner, serviços de aplicativo do Azure fornece uma ótima maneira de fornecer serviços de contêiner único escalonáveis.

Usar o serviço de aplicativo do Azure é intuitiva e você pode obter e em execução rapidamente, porque ele fornece excelente Git integração entrem em seu código, compile-o no Microsoft Visual Studio e implantá-la diretamente do Azure. Mas, tradicionalmente (com nenhuma Docker), se precisar de outros recursos, estruturas ou dependências que não têm suporte nos serviços de aplicativo, é necessário aguardar até que a equipe do Azure atualiza essas dependências no serviço de aplicativo ou alternado para outros serviços, como Service Fabric, serviços de nuvem ou até mesmo simples VMs, para que você tenha mais controle e pode instalar um componente necessário ou a estrutura do seu aplicativo.

Agora, no entanto, (anunciadas no Microsoft Connect 2016 em novembro de 2016) e conforme mostrado na Figura 4‑4, ao usar o Visual Studio de 2017, o suporte de contêiner no serviço de aplicativo do Azure oferece a capacidade de incluir tudo o que você deseja em seu ambiente de aplicativo. Se você adicionou uma dependência ao seu aplicativo, como você o está executando em um contêiner, você receberá a capacidade de incluir essas dependências em sua imagem Dockerfile ou Docker.

![](./media/image4.png)

Figura 4-4: publicar um contêiner para o serviço de aplicativo do Azure de aplicativos do Visual Studio/contêineres

Figura 4-4 também mostra o fluxo de publicação envia uma imagem por meio de um registro de contêiner, que pode ser o registro de contêiner do Azure (um registro de perto para suas implantações no Azure e protegido por contas e grupos do Active Directory do Azure) ou qualquer outro registro de Docker como os registros de Hub do Docker ou local.


>[!div class="step-by-step"]
[Anterior] (comum-contêiner-design-principles.md) [Avançar] (state-and-data-in-docker-applications.md)
