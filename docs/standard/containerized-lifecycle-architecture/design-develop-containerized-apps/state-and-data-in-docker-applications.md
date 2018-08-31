---
title: Estado e dados em aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 78db191bdec4c25c11728d819d89eaaaff4bd7da
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257351"
---
# <a name="state-and-data-in-docker-applications"></a>Estado e dados em aplicativos do Docker

Um primitivo de contêineres é imutabilidade. Quando comparado a uma VM, os contêineres não desaparecerem como uma ocorrência comum. Uma VM pode falhar em várias formas de processos inativos, sobrecarga da CPU ou um disco cheio ou com falha. Ainda assim, esperamos que a VM esteja disponível e unidades RAID são comuns para garantir que falhas de unidade mantêm os dados.

No entanto, contêineres forem considerados instâncias dos processos. Um processo não mantém o estado durável. Mesmo que um contêiner pode gravar em seu armazenamento local, supondo que essa instância permanecerá indefinidamente seria equivalente a supondo que uma cópia única de memória será durável. Você deve presumir que os contêineres, como processos, são duplicados, eliminado, ou, quando gerenciados com um orquestrador de contêiner, eles podem ser movidos.

Docker usa um recurso conhecido como um *sistema de arquivos de sobreposição* implementar um processo de cópia na gravação que armazena qualquer informações atualizadas sobre o sistema de arquivos raiz de um contêiner, em comparação comparado a imagem original na qual ele se baseia. Essas alterações serão perdidas se o contêiner for excluído posteriormente do sistema. Um contêiner, portanto, não tem armazenamento persistente por padrão. Embora seja possível salvar o estado de um contêiner, criação de um sistema em torno disso seria em conflito com o princípio de arquitetura do contêiner.

Para gerenciar dados persistentes em aplicativos do Docker, há soluções comuns:

-   [**Volumes de dados**](https://docs.docker.com/engine/tutorials/dockervolumes/) esses remontam ao host, conforme observado apenas.

-   [**Contêineres de volume de dados**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) eles fornecem armazenamento compartilhado em vários contêineres, usando um contêiner externo que pode ciclo.

-   [**Plug-ins de volume**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) esses montagem volumes em locais remotos, fornecendo a persistência de longo prazo.

-   **Fontes de dados remotas** exemplos incluem bancos de dados SQL e não-SQL ou armazenar em cache serviços, como o Redis.

-   [**O armazenamento do Azure**](https://docs.microsoft.com/azure/storage/) isso fornece a plataforma de distribuição geográfica como um armazenamento de serviço (PaaS), fornecendo o melhor dos contêineres de persistência de longo prazo como.

Volumes de dados são especialmente designados diretórios dentro de um ou mais contêineres que ignoram o [sistema de arquivos de união](https://docs.docker.com/glossary/?term=Union%20file%20system). Volumes de dados são projetados para manter os dados, independentemente do ciclo de vida do contêiner. Docker, portanto, nunca exclui automaticamente volumes quando você remove um contêiner, nem será volumes "coleta de lixo" que não são mais referenciados por um contêiner ele. Sistema operacional do host pode procurar e editar os dados em qualquer volume livremente, que é apenas outro motivo para usar volumes de dados com moderação.

Um [contêiner de volume de dados](https://docs.docker.com/glossary/?term=volume) é uma melhoria em relação a volumes de dados regulares. Ele é essencialmente um contêiner inativo que tem um ou mais volumes de dados criados dentro dele (conforme descrito anteriormente). O contêiner de volume de dados dá acesso aos contêineres de um ponto de montagem central. A vantagem desse método de acesso é que abstrai o local dos dados originais, tornando o contêiner de dados de um ponto de montagem lógico. Ele também permite acessar os volumes de contêiner de dados para serem criados e destruídos, mantendo os dados persistentes em um contêiner dedicado de contêineres de "aplicativo".

Figura 4-5 mostra que os volumes Docker regulares podem ser colocados em armazenamento fora dos contêineres de si, mas dentro dos limites físicos de servidor/VM do host. *Volumes docker não tem a capacidade de usar um volume de um host de servidor/VM para outro*.

![](./media/image5.png)

Figura 4-5: volumes de dados e fontes de dados externas para aplicativos de contêineres/contêineres

Devido à incapacidade de gerenciar dados compartilhados entre contêineres executados em hosts físicos separados, é recomendável que você não use volumes para dados de negócios, a menos que o host do Docker é uma host fixa/VM, porque ao usar contêineres do Docker em um orquestrador, contêineres devem ser movidos de um para outro host, dependendo das otimizações a ser executada pelo cluster.

Portanto, os volumes de dados regulares são um bom mecanismo para trabalhar com arquivos de rastreamento, arquivos temporais ou qualquer conceito semelhante que não afetarão a consistência dos dados de negócios se ou quando seus contêineres são movidos entre vários hosts.

[Plug-ins de volume](https://docs.docker.com/engine/extend/plugins_volume/) fornecem dados em todos os hosts em um cluster. Embora nem todos os plug-ins de volume sejam criados igualmente, o plug-ins de volume normalmente fornecem armazenamento externo persistente confiável externalizado dos contêineres imutáveis.

Fontes de dados remotas e caches, como banco de dados SQL, DocumentDB ou um cache remoto como o Redis seria o mesmo que o desenvolvimento sem contêineres. Essa é uma das maneiras preferenciais e comprovadas, para armazenar dados de aplicativo de negócios.


>[!div class="step-by-step"]
[Anterior](monolithic-applications.md)
[Próximo](soa-applications.md)
