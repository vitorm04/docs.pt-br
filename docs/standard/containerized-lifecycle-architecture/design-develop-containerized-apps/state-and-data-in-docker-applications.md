---
title: Estado e dados em aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b27be902779c7e22a568c679362851f745ea494d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569675"
---
# <a name="state-and-data-in-docker-applications"></a>Estado e dados em aplicativos do Docker

Um primitivo de contêineres é imutabilidade. Quando comparado a uma máquina virtual, os contêineres não desapareceram como uma ocorrência comum. Uma VM pode falhar em várias formas de processos inativos, sobrecarga da CPU ou um disco cheio ou com falha. Ainda, esperamos que a VM esteja disponível e unidades RAID são comuns para assegurar a mantêm os dados de falhas no disco.

No entanto, contêineres são considerados instâncias de processos. Um processo não manter o estado durável. Mesmo que um contêiner pode gravar em seu armazenamento local, supondo que essa instância será em torno indefinidamente seria equivalente supondo que uma única cópia de memória sejam durável. Você deve presumir que contêineres, como processos, duplicados, interrompido, ou, quando é gerenciado com o orchestrator um contêiner, eles podem ser movidos.

Docker usa um recurso conhecido como um *sobreposição de sistema de arquivos* implementar um processo de cópia na gravação que armazena quaisquer informações atualizadas ao sistema de arquivos raiz de um contêiner, em comparação comparado a imagem original no qual se baseia. Essas alterações serão perdidas se o contêiner subsequentemente é excluído do sistema. Um contêiner, portanto, não têm um armazenamento persistente por padrão. Embora seja possível salvar o estado de um contêiner, projetando um sistema isso seria em conflito com o princípio de arquitetura de contêiner.

Para gerenciar dados persistentes em aplicativos de Docker, há soluções comuns:

-   [**Volumes de dados**](https://docs.docker.com/engine/tutorials/dockervolumes/) esses de montagem para o host, conforme observado apenas.

-   [**Contêineres de volume de dados**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) elas fornecem armazenamento compartilhado entre contêineres, usando um contêiner externo que pode alternar.

-   [**Plug-ins do volume**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) esses montagem volumes em locais remotos, fornecendo a persistência de longo prazo.

-   **Fontes de dados remotas** exemplos incluem bancos de dados SQL e não-SQL ou serviços, como o Redis de cache.

-   [**Armazenamento do Azure**](https://docs.microsoft.com/azure/storage/) isso fornece a plataforma de distribuição geográfica como um armazenamento de serviço (PaaS), fornecendo o melhor de contêineres de persistência como a longo prazo.

Volumes de dados são designados especialmente diretórios dentro de um ou mais contêineres que ignoram o [sistema de arquivos de união](https://docs.docker.com/v1.8/reference/glossary#union-file-system). Volumes de dados são projetados para manter os dados, independentes do ciclo de vida do contêiner. Docker, portanto, nunca exclui automaticamente os volumes quando você remove um contêiner, nem o ele volumes "coleta de lixo" que não são mais referenciados por um contêiner. O sistema operacional do host pode navegar e editar os dados em qualquer volume livremente, que é apenas outra razão para usar os volumes de dados com moderação.

Um [contêiner de volume de dados](https://docs.docker.com/v1.8/userguide/dockervolumes/) é um aprimoramento volumes de dados regulares. É essencialmente um contêiner inativo que tem um ou mais volumes de dados criados nele (conforme descrito anteriormente). O contêiner de volume de dados dá acesso aos contêineres de um ponto de montagem central. A vantagem desse método de acesso é que ele abstrai o local dos dados originais, tornando o contêiner de dados um ponto de montagem lógico. Ele também permite acessar os volumes de contêiner de dados para serem criados e destruídos mantendo os dados persistentes em um contêiner dedicado de contêineres de "aplicativo".

Figura 4-5 mostra que volumes de Docker regulares podem ser colocados em armazenamento fora os contêineres de si, mas dentro dos limites físicos do host VM do servidor. *Volumes docker não tem a capacidade de usar um volume de um host VM server para outro*.

![](./media/image5.png)

Figura 4-5: volumes de dados e fontes de dados externas para contêineres de aplicativos/contêineres

Devido a dificuldades para gerenciar dados compartilhados entre contêineres que são executados em hosts físicos separados, é recomendável que você não use volumes para dados de negócios, a menos que o host do Docker é uma host fixa/VM, porque ao usar contêineres do Docker em um orchestrator contêineres devem ser movidos de um para outro host, dependendo de otimizações para ser executada pelo cluster.

Portanto, os volumes de dados regulares são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporal ou nenhum conceito semelhante que não afeta a consistência de dados de negócios se ou quando os contêineres são movidos em vários hosts.

Como o volume de plug-ins [Flocker](https://clusterhq.com/flocker/) fornecem dados em todos os hosts em um cluster. Embora nem todos os plug-ins de volume sejam criados igualmente, plug-ins do volume normalmente fornecem externalizado armazenamento confiável persistente dos contêineres imutável.

Fontes de dados remotas e caches como banco de dados SQL, documentos ou um cache remoto como Redis seria o mesmo que desenvolver sem contêineres. Essa é uma das maneiras preferenciais e testadas, para armazenar dados de aplicativo de negócios.


>[!div class="step-by-step"]
[Anterior] (monolítico-applications.md) [Avançar] (applications.md soa)
