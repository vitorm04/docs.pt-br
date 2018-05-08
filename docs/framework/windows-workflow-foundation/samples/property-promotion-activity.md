---
title: Atividade da promoção de propriedade
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 46e74c8c479e545778db92e15de3cb8798dafa11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="property-promotion-activity"></a>Atividade da promoção de propriedade
Este exemplo fornece uma solução ponta a ponta que integre o recurso de promoção de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> diretamente na experiência de criação de fluxo de trabalho. Uma coleção de elementos de configuração, as atividades de fluxo de trabalho, e as extensões de fluxo de trabalho que simplificam o uso de recurso da promoção são fornecidas. Além disso, o exemplo contém um fluxo de trabalho simples que demonstra como usar essa coleção.  
  
> [!NOTE]
>  Exemplos são fornecidos para fins educacionais somente. Não são destinados para um ambiente de produção, e não foram testados em um ambiente de produção. Microsoft não fornece suporte técnico para esses exemplos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
-   Um base de dados inicializado de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a>Projetos de exemplo  
  
-   O **PropertyPromotionActivity** projeto contém arquivos pertencentes a elementos de configuração específicas de promoção, atividades de fluxo de trabalho e extensões de fluxo de trabalho.  
  
-   O **CounterServiceApplication** projeto contém um fluxo de trabalho de exemplo que usa o **SqlWorkflowInstanceStorePromotion** projeto.  
  
-   Um script SQL (PropertyPromotionActivitySQLSample.sql) que deve ser executado com o base de dados de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .  
  
-   Um arquivo de solução que vincula os dois projetos de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (`PropertyPromotionActivity.sln`)  
  
## <a name="to-set-up-and-run-the-sample"></a>Para configurar e executar o exemplo  
  
1.  Inicializar uma base de dados de persistência de fluxo de trabalho.  
  
    1.  Navegue para o diretório de exemplo (\ \ WF básico \ \ PropertyPromotionActivity persistência) e a CreateInstanceStore.cmd executado.  
  
    2.  Se os privilégios de administrador não estão disponíveis, crie um login SQL Server. No SQL Server Management Studio, vá para **segurança**, **logons**. Clique com botão direito **logons** e crie um novo logon. Adicionar o usuário ACL para a função SQL abrindo **bancos de dados**, **InstanceStore**, **segurança**. Clique com botão direito **usuários** e selecione **novo usuário**. Definir o **nome de logon** para o usuário criado anteriormente. Adicione o usuário à função de associação System.Activities.DurableInstancing.InstanceStoreUsers (e outros) de base de dados. Observe que o usuário pode existir ainda (por exemplo, dbo de usuário).  
  
2.  Abra o arquivo de solução de PropertyPromotionActivity.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Se você criou o armazenamento de instância em uma base de dados que não seja uma instalação local do SQL Server Express edition, você deve atualizar a cadeia de conexão caracteres de base de dados. Alterar o arquivo App. config sob o **CounterServiceApplication** definindo o valor da `connectionString` atributo no `sqlWorkflowInstanceStorePromotion` nó para que ele aponte para o banco de dados de persistência que foi inicializado na etapa 1.  
  
4.  Criar e executar a solução. Isso enfiará o serviço do contador WF e iniciará automaticamente uma instância de fluxo de trabalho.  
  
5.  Selecione rapidamente todas as linhas em dbo []. O modo de CounterService [] em seu base de dados de persistência (esta exibição foi adicionada executando CreateInstanceStore.cmd na etapa 1). Você verá um conjunto de resultados semelhante ao seguinte:  
  
    |InstanceId|CounterValue|CounterValueLastUpdated|  
    |----------------|------------------|-----------------------------|  
    |2FA2C302-929E-4C0D-8C25-768A3DA20CE5|12|2010-02-18 22:48:01.740|  
  
     Porque você mantiver atualizar a exibição, você observará que o CounterValue e CounterValueLastUpdated alteram cada dois segundos. Este é o intervalo em que o contador se atualiza. O CounterValue e CounterValueLastUpdated representam propriedades elevadas para esse fluxo de trabalho.  
  
## <a name="to-remove-the-sample"></a>Para remover o exemplo  
  
-   Execução RemoveInstanceStore.cmd no diretório de exemplo (\ \ WF básico \ \ PropertyPromotionActivity persistência).  
  
## <a name="understanding-this-sample"></a>Entender este exemplo  
 O exemplo contém dois projetos e um arquivo SQL:  
  
-   **CounterServiceApplication** é um aplicativo de console que hospeda um serviço simples do WF do contador. Em cima de receber uma mensagem unidirecional através do ponto final de `Start` , o fluxo de trabalho conta 0 a 29, incremento uma variável de contagem cada dois segundos. Após cada incremento disso, o fluxo de trabalho persistir, e as propriedades elevadas são atualizados no dbo []. O modo de CounterService []. Quando o aplicativo de console é executado, hospeda o serviço de WF e envia uma mensagem ao ponto final de `Start` , criando uma instância do contador WF.  
  
-   **PropertyPromotionActivity** é uma biblioteca de classe que contém os elementos de configuração, as atividades de fluxo de trabalho e extensões de fluxo de trabalho que o **CounterServiceApplication** usa.  
  
-   **PropertyPromotionActivitySQLSample.sql** cria e adiciona o modo de exibição [dbo]. [ CounterService] para o banco de dados.  
  
### <a name="counterserviceapplication"></a>CounterServiceApplication  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a>Usando o elemento de configuração SqlWorkflowInstanceStorePromotion  
 O elemento de configuração `SqlWorkflowInstanceStorePromotion` herda do elemento de configuração `SqlWorkflowInstanceStore` , mas adiciona um elemento de configuração adicional chamado `promotionSets`. O elemento de `promotionSets` permite que o usuário para especificar propriedades elevadas com a configuração. Este é o arquivo de configuração que é usado por exemplo:  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 Examine a definição para dbo []. O modo de CounterService [].  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 Quando uma instância de fluxo de trabalho persistir, uma linha está inserida no modo de `InstancePromotedProperties` para cada `PromotionSet` definida na configuração. Esta linha contém todas as propriedades elevadas de `PromotionSet` (uma propriedade promovida pela coluna). Este `PromotionSet` é fechado por tuple: `InstanceId, PromotionName`. Nesse exemplo, temos um `PromotionSet` definido na configuração cujo atributo de nome é `CounterService`. Observe como o valor da coluna de `PromotionName` é igual ao atributo nome do elemento de `PromotionSet` .  
  
 A ordem dos elementos de `promotedValue` correlaciona com o posicionamento propriedades elevadas no modo de `InstancePromotedProperties` . `Count` é o primeiro elemento de `promotedValue` . Como resultado, é mapeado para a coluna de `Value1` no modo de `InstancePromotedProperties` . `LastIncrementedAt` é o segundo elemento de `promotedValue` . Como resultado, é mapeado para a coluna de `Value2` no modo de `InstancePromotedProperties` .  
  
#### <a name="using-the-promotevalue-activity"></a>Usando a atividade de PromoteValue  
 Examine o arquivo CounterService.xamlx no Designer de base de fluxo de trabalho do Windows. Observe que há duas atividades especiais na definição de WF: `PromoteValue<DateTime>` e `PromoteValue<Int32>`.  
  
 A atividade de `PromoteValue<Int32>` tem seu membro de `Name` definido como `Count`. Isso corresponde com o primeiro elemento de `promotedValue` na configuração, e tem seu `Value` definida como a variável de fluxo de trabalho de `Counter` . Quando o fluxo de trabalho persistir, a variável de fluxo de trabalho de `Counter` é persistida como uma propriedade promovida na coluna de `Value1` do modo de `InstancePromotedProperties` .  
  
 A atividade de `PromoteValue<DateTime>` tem seu membro de `Name` definido como `LastIncrementedAt`. Isso corresponde com o segundo elemento de `promotedValue` na configuração, e tem seu `Value` definida como a variável de fluxo de trabalho de `TimeLastIncremented` . Isso significa que quando o fluxo de trabalho persistir, o valor da variável de fluxo de trabalho de `TimeLastIncremented` será persistente como uma propriedade promovida na coluna de `Value2` do modo de `InstancePromotedProperties` .  
  
 Observe que a atividade de `PromotedValue` também tem um membro chamado booleano `ClearExistingPromotedData`. Quando esse membro é definido como `true`, este limpa todos os valores de propriedade elevados até esse ponto no fluxo de trabalho. Por exemplo, se uma atividade da sequência é definida como segue:  
  
1.  PromoteValue {nome = "Conta", valor = 3}  
  
2.  PromoteValue {nome = "LastIncrementedAt", valor = 1-1-2000}  
  
3.  Persistir  
  
4.  PromoteValue {nome = "Conta", valor = 4, ClearExistingPromotedData = true}  
  
5.  Persistir  
  
 No segundo persistir, o valor alto para `Count` será 4. No entanto, o valor promovido para `LastIncrementedAt` será `NULL`. Se `ClearExistingPromotedData` não foi definido como `true` para a etapa 4, então após o segundo persistir, o valor alto para a contagem seria 4. Como resultado, o valor alto para `LastIncrementedAt` seria ainda 1-1-2000.  
  
### <a name="propertypromotionactivity"></a>PropertyPromotionActivity  
 Esta biblioteca de classe contém as seguintes classes públicas para simplificar o uso de recurso da promoção de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> .  
  
#### <a name="promotevalue-class"></a>Classe de PromoteValue  
 Essa classe promove uma propriedade. O nome da propriedade promovida deve corresponder um atributo nome de um elemento de `promotedValue` na configuração. Esta atividade pode ser usada em Designer de Fluxo de Trabalho. Consulte o CounterServiceApplication para um uso de exemplo.  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 ClearExistingPromotedData (Bool)  
 Limpa todos os valores que foram valores antes desta atividade.  
  
 Nome (cadeia de caracteres)  
 O nome que representa a propriedade. Isso deve corresponder o atributo de nome de um \<promotedValue > elemento na configuração.  
  
 Valor (InArgument\<T >)  
 A variável/valor que você deseja armazenar na coluna.  
  
#### <a name="promotevalues-class"></a>Classe de PromoteValues  
 Promove várias propriedades. Os nomes das propriedades elevadas devem corresponder todos os atributos de nome em elementos de `promotedValue` na configuração. O uso é semelhante à atividade de `PromoteValue` , exceto pelo fato de que as várias propriedades podem ser elevadas ao mesmo tempo. Esta atividade não pode ser usada em Designer de Fluxo de Trabalho.  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a>SqlWorkflowInstanceStorePromotionBehavior  
 Deriva de `SqlWorkflowInstanceStoreBehavior`. Essa classe derivada adiciona um participante personalizado de persistência (também uma parte desta biblioteca) como uma extensão de fluxo de trabalho. A implementação das atividades anteriores de fluxo de trabalho confia neste participante personalizado de persistência.  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 Esta biblioteca de classes também contém a implementação de `ConfigurationElement` para `SqlWorkflowInstanceStorePromotionElement` e um participante personalizado de persistência usado por atividades anteriores da promoção.  
  
### <a name="propertypromotionactivitysqlsample"></a>PropertyPromotionActivitySQLSample  
 Este arquivo SQL cria um modo de exibição de `[dbo].[CounterService]` além da o modo de `[InstancePromotedProperties]` para ver todas as instâncias que têm uma promoção de CounterService definida.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verificar o seguinte diretório (padrão) antes de continuar:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está no seguinte diretório:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
