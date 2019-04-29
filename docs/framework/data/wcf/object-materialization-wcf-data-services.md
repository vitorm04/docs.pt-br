---
title: Materialização de objeto (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: bf75e126c2a44b6b9d151269046d2cb8110815cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774680"
---
# <a name="object-materialization-wcf-data-services"></a>Materialização de objeto (WCF Data Services)
Quando você usa o **adicionar referência de serviço** caixa de diálogo para consumir um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed em um aplicativo cliente com base no .NET Framework, classes de dados equivalentes são geradas para cada tipo de entidade no modelo de dados exposto pelo feed. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Dados de entidade que são retornados por uma consulta são materializados em uma instância de uma dessas classes de serviço de dados do cliente gerado. Para obter informações sobre opções de mesclagem e a resolução de identidade para objetos acompanhados, consulte [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também permite que você defina suas próprias classes de serviço de dados do cliente em vez de usar as classes de dados gerados por ferramenta. Isso permite que você use suas próprias classes de dados, também conhecido como "objeto CLR BOM e velho" classes de dados (POCO). Ao usar esses tipos de classes de dados personalizados, você deve atributo a classe de dados com um <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> e certifique-se de que nomes de tipo nos nomes de tipo de correspondência de cliente no modelo de dados do serviço de dados.  
  
 Depois que a biblioteca recebe a mensagem de resposta de consulta, ele materializa os dados retornados do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] classes de serviço que são do tipo da consulta de feed em instâncias de dados do cliente. O processo geral para materializar desses objetos é da seguinte maneira:  
  
1. A biblioteca de cliente lê o tipo serializado do `entry` elemento na mensagem de resposta de feed e tenta criar uma nova instância do tipo correto, em uma das seguintes maneiras:  
  
    - Quando o tipo declarado no feed tem o mesmo nome como o tipo do <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância desse tipo é criada usando o construtor vazio.  
  
    - Quando o tipo declarado no feed tem o mesmo nome como um tipo que é derivado do tipo do <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância desse tipo derivada é criada usando o construtor vazio.  
  
    - Quando o tipo declarado no feed não é possível corresponder ao tipo do <xref:System.Data.Services.Client.DataServiceQuery%601> ou quaisquer tipos derivados, uma nova instância do tipo consultado é criada usando o construtor vazio.  
  
    - Quando o <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> estiver definida, o delegado fornecido é chamado para substituir o mapeamento de tipo com base no nome padrão e uma nova instância do tipo retornado pelo <xref:System.Func%602> é criado em seu lugar. Se esse delegado retorna um valor nulo, uma nova instância do tipo consultado é criada em vez disso. Pode ser necessário substituir o mapeamento de nome de tipo com base no nome padrão para dar suporte a cenários de herança.  
  
2. A biblioteca de cliente lê o valor do URI do `id` elemento o `entry`, que é o valor de identidade da entidade. A menos que um <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> valor de <xref:System.Data.Services.Client.MergeOption.NoTracking> é usado, o valor de identidade é usado para acompanhar o objeto no <xref:System.Data.Services.Client.DataServiceContext>. O valor de identidade também é usado para garantir que apenas uma instância de entidade única é criada, mesmo quando uma entidade for retornada várias vezes na resposta da consulta.  
  
3. A biblioteca de cliente lê as propriedades na entrada do feed e definir as propriedades correspondentes no objeto recém-criado. Quando um objeto que tem o mesmo valor de identidade já ocorre na <xref:System.Data.Services.Client.DataServiceContext>, as propriedades são definidas com base no <xref:System.Data.Services.Client.MergeOption> configuração do <xref:System.Data.Services.Client.DataServiceContext>. A resposta pode conter valores de propriedade para o qual uma propriedade correspondente não ocorre no tipo de cliente. Quando isso ocorrer, a ação depende do valor da <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriedade do <xref:System.Data.Services.Client.DataServiceContext>. Quando essa propriedade é definida como `true`, a propriedade ausente será ignorada. Caso contrário, ocorrerá um erro. Propriedades são definidas da seguinte maneira:  
  
    - Propriedades escalares são definidas como o valor correspondente na entrada na mensagem de resposta.  
  
    - Propriedades complexas são definidas para uma nova instância de tipo complexo, que são definidas com as propriedades do tipo complexo da resposta.  
  
    - Propriedades de navegação que retornam uma coleção de entidades relacionadas são definidas para uma instância nova ou existente do <xref:System.Collections.Generic.ICollection%601>, onde `T` é o tipo da entidade relacionada. Esta coleção está vazia, a menos que os objetos relacionados foram carregados no <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [Carregando conteúdo adiado](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Quando as classes de dados do cliente gerado dá suporte a vinculação de dados, as propriedades de navegação retornam instâncias da <xref:System.Data.Services.Client.DataServiceCollection%601> classe em vez disso. Para obter mais informações, consulte [associando dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4. O <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> é gerado.  
  
5. A biblioteca de cliente anexa o objeto a ser o <xref:System.Data.Services.Client.DataServiceContext>. O objeto não está anexado quando o <xref:System.Data.Services.Client.MergeOption> é <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Consulte também

- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
- [Projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
