---
title: Expressions1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18c64daca1532bb626a59e5f01528e207e6b6b87
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="expressions"></a><span data-ttu-id="e44b6-102">Expressões</span><span class="sxs-lookup"><span data-stu-id="e44b6-102">Expressions</span></span>
<span data-ttu-id="e44b6-103">Uma expressão do Windows Workflow Foundation (WF) é qualquer atividade que retorna um resultado.</span><span class="sxs-lookup"><span data-stu-id="e44b6-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="e44b6-104">Todas as atividades de expressão derivam indiretamente de <xref:System.Activities.Activity%601>, que contém uma propriedade de <xref:System.Activities.OutArgument> nomeada <xref:System.Activities.Activity%601.Result%2A> como o valor de retorno da atividade.</span><span class="sxs-lookup"><span data-stu-id="e44b6-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> <span data-ttu-id="e44b6-105">O [!INCLUDE[wf1](../../../includes/wf1-md.md)] é fornecido com uma ampla gama de atividades de expressão simples como <xref:System.Activities.Expressions.VariableValue%601> e <xref:System.Activities.Expressions.VariableReference%601>, que fornecem acesso à variável única de fluxo de trabalho por meio de atividades do operador, a atividades complexas como <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> e <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> que oferecem acesso à largura máxima da linguagem Visual Basic para produzir o resultado.</span><span class="sxs-lookup"><span data-stu-id="e44b6-105">[!INCLUDE[wf1](../../../includes/wf1-md.md)] ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="e44b6-106">As atividades adicionais da expressão podem ser criadas derivando de <xref:System.Activities.CodeActivity%601> ou <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="e44b6-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="e44b6-107">Usando expressões</span><span class="sxs-lookup"><span data-stu-id="e44b6-107">Using Expressions</span></span>  
 <span data-ttu-id="e44b6-108">O designer de fluxo de trabalho usa <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> e <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> para todas as expressões em projetos do Visual Basic, e <xref:Microsoft.CSharp.Activities.CSharpValue%601> e <xref:Microsoft.CSharp.Activities.CSharpReference%601> para expressões em projetos de fluxo de trabalho C#.</span><span class="sxs-lookup"><span data-stu-id="e44b6-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e44b6-109">O suporte para expressões C# em projetos de fluxo de trabalho foi introduzido no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e44b6-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="e44b6-110">Para obter mais informações, consulte [c# expressões](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e44b6-110">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="e44b6-111">Os fluxos de trabalho gerados pelo designer são salvos em XAML, onde as expressões aparecem incluídas entre colchetes, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e44b6-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 <span data-ttu-id="e44b6-112">Ao definir um fluxo de trabalho em código, as atividades de expressão podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="e44b6-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="e44b6-113">O exemplo a seguir mostra o uso de uma combinação de atividades do operador para adicionar três números.</span><span class="sxs-lookup"><span data-stu-id="e44b6-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 <span data-ttu-id="e44b6-114">O mesmo fluxo de trabalho pode ser expresso de modo mais compacto usando expressões lambda C#, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e44b6-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="e44b6-115">O fluxo de trabalho também pode ser expresso usando atividades de expressão do Visual Basic, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e44b6-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="e44b6-116">Estendendo expressões disponíveis com atividades da expressão personalizadas</span><span class="sxs-lookup"><span data-stu-id="e44b6-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="e44b6-117">As expressões no [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] são extensível permitindo atividades adicionais da expressão a serem criadas.</span><span class="sxs-lookup"><span data-stu-id="e44b6-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="e44b6-118">O exemplo a seguir mostra uma atividade que retorna uma soma de três valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="e44b6-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="e44b6-119">Com essa nova atividade, você pode reescrever o fluxo de trabalho anterior que adicionou três valores conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e44b6-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e44b6-120"> usando expressões no código, consulte [criação de fluxos de trabalho, atividades e expressões usando imperativo código](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span><span class="sxs-lookup"><span data-stu-id="e44b6-120"> using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
