---
title: Materialização de objeto (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 89357b1d05526438c939a73663c5b7b6273df4ac
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790395"
---
# <a name="object-materialization-wcf-data-services"></a>Materialização de objeto (WCF Data Services)

Quando você usa a caixa de diálogo **Adicionar referência de serviço** para [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] consumir um feed em um aplicativo cliente baseado em .NET Framework, classes de dados equivalentes são geradas para cada tipo de entidade no modelo de dados exposto pelo feed. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](generating-the-data-service-client-library-wcf-data-services.md). Os dados de entidade que são retornados por uma consulta são materializados em uma instância de uma dessas classes de serviço de dados do cliente geradas. Para obter informações sobre opções de mesclagem e resolução de identidade para objetos rastreados, consulte [Gerenciando o contexto do serviço de dados](managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]também permite que você defina suas próprias classes de serviço de dados de cliente em vez de usar as classes de dados geradas por ferramentas. Isso permite que você use suas próprias classes de dados, também conhecidas como classes de dados "POCO (objeto CLR) simples. Ao usar esses tipos de classes de dados personalizadas, você deve atribuir a classe de dados <xref:System.Data.Services.Common.DataServiceKeyAttribute> com <xref:System.Data.Services.Common.DataServiceEntityAttribute> um ou e garantir que os nomes de tipo no cliente correspondam aos nomes de tipo no modelo de dados do serviço de dados.

Depois que a biblioteca recebe a mensagem de resposta de consulta, ela materializa os dados retornados [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do feed em instâncias de classes de serviço de dados do cliente que são do tipo da consulta. O processo geral para materialização desses objetos é o seguinte:

1. A biblioteca de cliente lê o tipo serializado do `entry` elemento no feed de mensagens de resposta e tenta criar uma nova instância do tipo correto, de uma das seguintes maneiras:

    - Quando o tipo declarado no feed tem o mesmo nome que o tipo de <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância desse tipo é criada usando o construtor vazio.

    - Quando o tipo declarado no feed tem o mesmo nome que um tipo derivado do tipo de <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância desse tipo derivado é criada usando o construtor vazio.

    - Quando o tipo declarado no feed não puder ser correspondido ao tipo do <xref:System.Data.Services.Client.DataServiceQuery%601> ou qualquer tipo derivado, uma nova instância do tipo consultado será criada usando o construtor vazio.

    - Quando a <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> propriedade é definida, o delegado fornecido é chamado para substituir o mapeamento de tipo baseado em nome padrão e uma nova instância do tipo retornado <xref:System.Func%602> pelo é criada em seu lugar. Se esse delegado retornar um valor nulo, uma nova instância do tipo consultado será criada em vez disso. Pode ser necessário substituir o mapeamento de nome de tipo baseado em nome padrão para dar suporte a cenários de herança.

2. A biblioteca de cliente lê o valor do URI `id` a partir do `entry`elemento de, que é o valor de identidade da entidade. A menos <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> que um <xref:System.Data.Services.Client.MergeOption.NoTracking> valor de seja usado, o valor de identidade é usado para <xref:System.Data.Services.Client.DataServiceContext>rastrear o objeto no. O valor de identidade também é usado para garantir que apenas uma única instância de entidade seja criada, mesmo quando uma entidade é retornada várias vezes na resposta da consulta.

3. A biblioteca de cliente lê as propriedades da entrada do feed e define as propriedades correspondentes no objeto recém-criado. Quando um objeto que tem o mesmo valor de identidade já ocorre no <xref:System.Data.Services.Client.DataServiceContext>, as propriedades são definidas com base <xref:System.Data.Services.Client.MergeOption> na configuração do <xref:System.Data.Services.Client.DataServiceContext>. A resposta pode conter valores de propriedade para os quais uma propriedade correspondente não ocorre no tipo de cliente. Quando isso ocorre, a ação depende do valor <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> da propriedade <xref:System.Data.Services.Client.DataServiceContext>do. Quando essa propriedade é definida como `true`, a propriedade Missing é ignorada. Caso contrário, um erro será gerado. As propriedades são definidas da seguinte maneira:

    - As propriedades escalares são definidas para o valor correspondente na entrada na mensagem de resposta.

    - As propriedades complexas são definidas para uma nova instância de tipo complexo, que são definidas com as propriedades do tipo complexo da resposta.

    - As propriedades de navegação que retornam uma coleção de entidades relacionadas são definidas como uma instância nova <xref:System.Collections.Generic.ICollection%601>ou existente `T` do, em que é o tipo da entidade relacionada. Essa coleção está vazia, a menos que os objetos relacionados tenham sido <xref:System.Data.Services.Client.DataServiceContext>carregados no. Para obter mais informações, consulte [carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Quando as classes de dados de cliente geradas dão suporte à vinculação de dados, <xref:System.Data.Services.Client.DataServiceCollection%601> as propriedades de navegação retornam instâncias da classe em vez disso. Para obter mais informações, consulte [associando dados a controles](binding-data-to-controls-wcf-data-services.md).

4. O <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> evento é gerado.

5. A biblioteca de cliente anexa o objeto ao <xref:System.Data.Services.Client.DataServiceContext>. O objeto não está anexado quando o <xref:System.Data.Services.Client.MergeOption> é <xref:System.Data.Services.Client.MergeOption.NoTracking>.

## <a name="see-also"></a>Consulte também

- [Querying the Data Service](querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
- [Projeções de consulta](query-projections-wcf-data-services.md)
