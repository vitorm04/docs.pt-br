---
title: Materialização de objetos (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 54f8cc876b373fcfa8e8e514abf50111942de88c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365456"
---
# <a name="object-materialization-wcf-data-services"></a>Materialização de objetos (WCF Data Services)
Quando você usa o **adicionar referência de serviço** caixa de diálogo para consumir um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed em um aplicativo cliente com base no .NET Framework, classes de dados equivalentes são gerados para cada tipo de entidade no modelo de dados exposto pelo feed. Para obter mais informações, consulte [gerando a biblioteca de cliente do serviço de dados](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Dados de entidade que são retornados por uma consulta estão materializados em uma instância de uma dessas classes de serviço de dados de cliente gerada. Para obter informações sobre opções de mesclagem e a resolução de identidade para objetos rastreados, consulte [Gerenciando o contexto do serviço de dados](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] também permite que você defina suas próprias classes de serviço de dados do cliente em vez de usar as classes de dados gerados por ferramenta. Isso permite que você use suas próprias classes de dados, também conhecido como "objeto CLR plain old" classes de dados (POCO). Ao usar esses tipos de classes de dados personalizados, você deve atributo classe de dados com um <xref:System.Data.Services.Common.DataServiceKeyAttribute> ou <xref:System.Data.Services.Common.DataServiceEntityAttribute> e certifique-se de que o tipo de nomes nos nomes de tipo de correspondência de cliente no modelo de dados do serviço de dados.  
  
 Depois que a biblioteca de recebe a mensagem de resposta de consulta, ele materializa os dados retornados do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] classes de serviço que são do tipo de consulta de feed em instâncias de dados do cliente. O processo geral para materializar desses objetos é da seguinte maneira:  
  
1.  A biblioteca de cliente lê o tipo serializado do `entry` elemento na mensagem de resposta de feed e tenta criar uma nova instância do tipo correto, em uma das seguintes maneiras:  
  
    -   Quando o tipo declarado no feed tem o mesmo nome como o tipo do <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância desse tipo é criada usando o construtor vazio.  
  
    -   Quando o tipo declarado no feed tem o mesmo nome como um tipo que é derivado do tipo do <xref:System.Data.Services.Client.DataServiceQuery%601>, uma nova instância deste tipo derivado é criada usando o construtor vazio.  
  
    -   Quando o tipo declarado no feed não corresponde ao tipo do <xref:System.Data.Services.Client.DataServiceQuery%601> ou qualquer tipos derivados, uma nova instância do tipo consultado é criada usando o construtor vazio.  
  
    -   Quando o <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> estiver definida, o delegado fornecido é chamado para substituir o mapeamento de tipo baseado no nome padrão e uma nova instância do tipo retornado pelo <xref:System.Func%602> será criada. Se este delegado retorna um valor nulo, será criada uma nova instância do tipo consultado. Pode ser necessário substituir o mapeamento de nome padrão baseado no nome de tipo para dar suporte a cenários de herança.  
  
2.  A biblioteca de cliente lê o valor do URI do `id` elemento o `entry`, que é o valor de identidade da entidade. A menos que um <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> valor <xref:System.Data.Services.Client.MergeOption.NoTracking> é usado, o valor de identidade é usado para controlar o objeto no <xref:System.Data.Services.Client.DataServiceContext>. O valor de identidade também é usado para garantir que apenas uma instância de entidade única é criada, mesmo quando uma entidade for retornada várias vezes na resposta da consulta.  
  
3.  A biblioteca de cliente lê propriedades de entrada de feed e definir as propriedades correspondentes no objeto recém-criado. Quando um objeto que tem o mesmo valor de identidade já ocorre no <xref:System.Data.Services.Client.DataServiceContext>, as propriedades são definidas com base no <xref:System.Data.Services.Client.MergeOption> configuração do <xref:System.Data.Services.Client.DataServiceContext>. A resposta pode conter valores de propriedade para o qual uma propriedade correspondente não ocorre no tipo de cliente. Quando isso ocorre, a ação depende do valor da <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> propriedade o <xref:System.Data.Services.Client.DataServiceContext>. Quando essa propriedade é definida como `true`, a propriedade ausente será ignorada. Caso contrário, ocorrerá um erro. Propriedades são definidas da seguinte maneira:  
  
    -   Propriedades escalares são definidas como o valor correspondente na entrada na mensagem de resposta.  
  
    -   Propriedades complexas são definidas para uma nova instância de tipo complexo, que são definidas com as propriedades do tipo complexo de resposta.  
  
    -   Propriedades de navegação que retorna uma coleção de entidades relacionadas são definidas para uma instância nova ou existente do <xref:System.Collections.Generic.ICollection%601>, onde `T` é o tipo da entidade relacionada. Essa coleção está vazia, a menos que os objetos relacionados tiverem sido carregados no <xref:System.Data.Services.Client.DataServiceContext>. Para obter mais informações, consulte [carregar conteúdo adiada](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Quando as classes de dados gerado de cliente oferecem suporte à associação de dados, propriedades de navegação retornarem instâncias da <xref:System.Data.Services.Client.DataServiceCollection%601> classe em vez disso. Para obter mais informações, consulte [vinculação de dados a controles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4.  O <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> é gerado.  
  
5.  A biblioteca de cliente anexa o objeto para o <xref:System.Data.Services.Client.DataServiceContext>. O objeto não está anexado quando a <xref:System.Data.Services.Client.MergeOption> é <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Consulte também  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)  
 [Projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
