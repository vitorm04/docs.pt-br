---
title: Argumentos necessários e grupos de sobrecarga
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d7cfe00d93f1eede77bcda5881c63843722c9a17
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374255"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="9eb66-102">Argumentos necessários e grupos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="9eb66-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="9eb66-103">As atividades podem ser configuradas de modo que determinados argumentos são necessários para ser associados para que a atividade é válido para a execução.</span><span class="sxs-lookup"><span data-stu-id="9eb66-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="9eb66-104">O atributo de `RequiredArgument` é usado para indicar que determinados argumentos em uma atividade são necessários e o atributo de `OverloadGroup` é usado para agrupar categorias de argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="9eb66-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="9eb66-105">Usando atributos, os autores de atividade podem fornecer configurações simples ou complexas de validação de atividade.</span><span class="sxs-lookup"><span data-stu-id="9eb66-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="9eb66-106">Usando argumentos necessários</span><span class="sxs-lookup"><span data-stu-id="9eb66-106">Using Required Arguments</span></span>  
 <span data-ttu-id="9eb66-107">Para usar o atributo de `RequiredArgument` em uma atividade, indica os argumentos desejados usando <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9eb66-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="9eb66-108">Nesse exemplo, uma atividade de `Add` é definida que possui dois argumentos necessários.</span><span class="sxs-lookup"><span data-stu-id="9eb66-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
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
  
 <span data-ttu-id="9eb66-109">Em XAML, os argumentos necessários são indicados também usando <xref:System.Activities.RequiredArgumentAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9eb66-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="9eb66-110">Nesse exemplo a atividade de `Add` é definida usando três argumentos e usa uma atividade de <xref:System.Activities.Statements.Assign%601> para executar a operação adicionar.</span><span class="sxs-lookup"><span data-stu-id="9eb66-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
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
  
 <span data-ttu-id="9eb66-111">Se a atividade é usada e qualquer um dos argumentos necessários não está associado ao seguinte erro de validação é retornado.</span><span class="sxs-lookup"><span data-stu-id="9eb66-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="9eb66-112">**Valor de um argumento necessário "operando1" de atividade não foi fornecido.**</span><span class="sxs-lookup"><span data-stu-id="9eb66-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="9eb66-113">Para obter mais informações sobre como verificar e tratamento de erros de validação e avisos, consulte [invocando a validação de atividade](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="9eb66-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="9eb66-114">Usando grupos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="9eb66-114">Using Overload Groups</span></span>

<span data-ttu-id="9eb66-115">Grupos de sobrecarga fornecem um método para indicar que combinações de argumentos são válidos em uma atividade.</span><span class="sxs-lookup"><span data-stu-id="9eb66-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="9eb66-116">Os argumentos são agrupados usando <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9eb66-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="9eb66-117">Cada grupo é dado um nome que é especificado pelo <xref:System.Activities.OverloadGroupAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9eb66-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="9eb66-118">A atividade é válida quando apenas um conjunto de argumentos em um grupo de sobrecarga está associado.</span><span class="sxs-lookup"><span data-stu-id="9eb66-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="9eb66-119">No exemplo a seguir, um `CreateLocation` classe é definida.</span><span class="sxs-lookup"><span data-stu-id="9eb66-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
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
  
 <span data-ttu-id="9eb66-120">O objetivo desta atividade é especificar um local nos EUA).</span><span class="sxs-lookup"><span data-stu-id="9eb66-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="9eb66-121">Para fazer isso, o usuário da atividade pode especificar o local usando um dos três grupos de argumentos.</span><span class="sxs-lookup"><span data-stu-id="9eb66-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="9eb66-122">Para especificar as combinações de argumentos, válidos três grupos de sobrecarga são definidos.</span><span class="sxs-lookup"><span data-stu-id="9eb66-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="9eb66-123">`G1` contém os argumentos de `Latitude` e de `Longitude` .</span><span class="sxs-lookup"><span data-stu-id="9eb66-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="9eb66-124">`G2` contém `Street`, `City`, e `State`.</span><span class="sxs-lookup"><span data-stu-id="9eb66-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="9eb66-125">`G3` contém `Street` e `Zip`.</span><span class="sxs-lookup"><span data-stu-id="9eb66-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="9eb66-126">`Name` é também um argumento necessário, mas não é parte de um grupo de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="9eb66-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="9eb66-127">Para que esta atividade é válida, `Name` terá que ser associado junto com todos os argumentos de um e somente um grupo de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="9eb66-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="9eb66-128">No exemplo a seguir, extraído do [atividades de acesso de banco de dados](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) exemplo, há dois grupos de sobrecarga: `ConnectionString` e `ConfigFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="9eb66-128">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="9eb66-129">Para que esta atividade é válida, ou outro os argumentos de `ProviderName` e de `ConnectionString` devem ser associados, ou o argumento de `ConfigName` , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="9eb66-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
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
  
 <span data-ttu-id="9eb66-130">Ao definir um grupo de sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="9eb66-130">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="9eb66-131">Um grupo de sobrecarga não pode ser um subconjunto ou um conjunto equivalente de outro grupo de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="9eb66-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9eb66-132">Há uma exceção a essa regra.</span><span class="sxs-lookup"><span data-stu-id="9eb66-132">There is one exception to this rule.</span></span> <span data-ttu-id="9eb66-133">Se um grupo de sobrecarga é um subconjunto de outro grupo de sobrecarga, e o subconjunto contém somente os argumentos onde `RequiredArgument` é `false`, então o grupo de sobrecarga é válido.</span><span class="sxs-lookup"><span data-stu-id="9eb66-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="9eb66-134">Grupos de sobrecarga podem sobrepor mas é um erro se a interseção de grupos contém todos os argumentos necessários de um ou ambos os grupos de sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="9eb66-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="9eb66-135">No exemplo anterior grupos de sobrecarga de `G2` e de `G3` sobrepors, mas porque a interseção não contém todos os argumentos de um ou ambos os grupos isso era válidos.</span><span class="sxs-lookup"><span data-stu-id="9eb66-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="9eb66-136">Ao associar argumentos em um grupo de sobrecarga:</span><span class="sxs-lookup"><span data-stu-id="9eb66-136">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="9eb66-137">Um grupo de sobrecarga está sendo associado se todos os argumentos de `RequiredArgument` no grupo são associados.</span><span class="sxs-lookup"><span data-stu-id="9eb66-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="9eb66-138">Se um grupo tem os argumentos de `RequiredArgument` zero e pelo menos um argumento associado, então o grupo está sendo associado.</span><span class="sxs-lookup"><span data-stu-id="9eb66-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="9eb66-139">É um erro de validação se nenhum grupo de sobrecarga é associado a menos que um grupo de sobrecarga não tem nenhum argumento de `RequiredArgument` nele.</span><span class="sxs-lookup"><span data-stu-id="9eb66-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="9eb66-140">É um erro para ter mais de um grupo de sobrecarga associada, isto é, todos os argumentos necessários em um grupo de sobrecarga é limitado e qualquer argumento em outro grupo de sobrecarga está associado também.</span><span class="sxs-lookup"><span data-stu-id="9eb66-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
