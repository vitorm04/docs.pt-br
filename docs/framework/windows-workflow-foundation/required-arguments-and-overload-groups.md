---
title: Argumentos necessários e grupos de sobrecarga
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47e94c65ff722d3b4f98b026d69ecd31bc02b934
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="required-arguments-and-overload-groups"></a>Argumentos necessários e grupos de sobrecarga
As atividades podem ser configuradas de modo que determinados argumentos são necessários para ser associados para que a atividade é válido para a execução. O atributo de `RequiredArgument` é usado para indicar que determinados argumentos em uma atividade são necessários e o atributo de `OverloadGroup` é usado para agrupar categorias de argumentos necessários. Usando atributos, os autores de atividade podem fornecer configurações simples ou complexas de validação de atividade.  
  
## <a name="using-required-arguments"></a>Usando argumentos necessários  
 Para usar o atributo de `RequiredArgument` em uma atividade, indica os argumentos desejados usando <xref:System.Activities.RequiredArgumentAttribute>. Nesse exemplo, uma atividade de `Add` é definida que possui dois argumentos necessários.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 Em XAML, os argumentos necessários são indicados também usando <xref:System.Activities.RequiredArgumentAttribute>. Nesse exemplo a atividade de `Add` é definida usando três argumentos e usa uma atividade de <xref:System.Activities.Statements.Assign%601> para executar a operação adicionar.  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 Se a atividade é usada e qualquer um dos argumentos necessários não está associado ao seguinte erro de validação é retornado.  
  
 **Valor de um argumento de atividade obrigatório 'Operando1' não foi fornecido.**  
> [!NOTE]
>  Para obter mais informações sobre sobre procurando e tratamento de erros de validação e avisos, consulte [invocando a validação de atividades](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).  
  
## <a name="using-overload-groups"></a>Usando grupos de sobrecarga  
 Grupos de sobrecarga fornecem um método para indicar que combinações de argumentos são válidos em uma atividade. Os argumentos são agrupados usando <xref:System.Activities.OverloadGroupAttribute>. Cada grupo é dado um nome que é especificado por <xref:System.Activities.OverloadGroupAttribute>, a atividade é válido somente quando um conjunto de argumentos em um grupo de sobrecarga está associado. No exemplo a seguir, retirado de [OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) exemplo, um `CreateLocation` classe é definida.  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 O objetivo desta atividade é especificar um local nos EUA). Para fazer isso, o usuário da atividade pode especificar o local usando um dos três grupos de argumentos. Para especificar as combinações de argumentos, válidos três grupos de sobrecarga são definidos. `G1` contém os argumentos de `Latitude` e de `Longitude` . `G2` contém `Street`, `City`, e `State`. `G3` contém `Street` e `Zip`. `Name` é também um argumento necessário, mas não é parte de um grupo de sobrecarga. Para que esta atividade é válida, `Name` terá que ser associado junto com todos os argumentos de um e somente um grupo de sobrecarga.  
  
 No exemplo a seguir, retirado de [atividades de acesso de banco de dados](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) exemplo, há dois grupos de sobrecargas: `ConnectionString` e `ConfigFileSectionName`. Para que esta atividade é válida, ou outro os argumentos de `ProviderName` e de `ConnectionString` devem ser associados, ou o argumento de `ConfigName` , mas não ambos.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 Ao definir um grupo de sobrecarga:  
  
-   Um grupo de sobrecarga não pode ser um subconjunto ou um conjunto equivalente de outro grupo de sobrecarga.  
  
    > [!NOTE]
    >  Há uma exceção a essa regra. Se um grupo de sobrecarga é um subconjunto de outro grupo de sobrecarga, e o subconjunto contém somente os argumentos onde `RequiredArgument` é `false`, então o grupo de sobrecarga é válido.  
  
-   Grupos de sobrecarga podem sobrepor mas é um erro se a interseção de grupos contém todos os argumentos necessários de um ou ambos os grupos de sobrecarga. No exemplo anterior grupos de sobrecarga de `G2` e de `G3` sobrepors, mas porque a interseção não contém todos os argumentos de um ou ambos os grupos isso era válidos.  
  
 Ao associar argumentos em um grupo de sobrecarga:  
  
-   Um grupo de sobrecarga está sendo associado se todos os argumentos de `RequiredArgument` no grupo são associados.  
  
-   Se um grupo tem os argumentos de `RequiredArgument` zero e pelo menos um argumento associado, então o grupo está sendo associado.  
  
-   É um erro de validação se nenhum grupo de sobrecarga é associado a menos que um grupo de sobrecarga não tem nenhum argumento de `RequiredArgument` nele.  
  
-   É um erro para ter mais de um grupo de sobrecarga associada, isto é, todos os argumentos necessários em um grupo de sobrecarga é limitado e qualquer argumento em outro grupo de sobrecarga está associado também.
