---
title: Expressions1
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 7643279c2db5608c028e0a1213802ab609a2d347
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773640"
---
# <a name="expressions"></a>Expressões
Uma expressão do Windows Workflow Foundation (WF) é qualquer atividade que retorna um resultado. Todas as atividades de expressão derivam indiretamente de <xref:System.Activities.Activity%601>, que contém uma propriedade de <xref:System.Activities.OutArgument> nomeada <xref:System.Activities.Activity%601.Result%2A> como o valor de retorno da atividade. O [!INCLUDE[wf1](../../../includes/wf1-md.md)] é fornecido com uma ampla gama de atividades de expressão simples como <xref:System.Activities.Expressions.VariableValue%601> e <xref:System.Activities.Expressions.VariableReference%601>, que fornecem acesso à variável única de fluxo de trabalho por meio de atividades do operador, a atividades complexas como <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> e <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> que oferecem acesso à largura máxima da linguagem Visual Basic para produzir o resultado. As atividades adicionais da expressão podem ser criadas derivando de <xref:System.Activities.CodeActivity%601> ou <xref:System.Activities.NativeActivity%601>.  
  
## <a name="using-expressions"></a>Usando expressões  
 O designer de fluxo de trabalho usa <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> e <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> para todas as expressões em projetos do Visual Basic, e <xref:Microsoft.CSharp.Activities.CSharpValue%601> e <xref:Microsoft.CSharp.Activities.CSharpReference%601> para expressões em projetos de fluxo de trabalho C#.  
  
> [!NOTE]
>  O suporte para expressões C# em projetos de fluxo de trabalho foi introduzido no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Para obter mais informações, consulte [ C# expressões](csharp-expressions.md).  
  
 Os fluxos de trabalho gerados pelo designer são salvos em XAML, onde as expressões aparecem incluídas entre colchetes, como no exemplo a seguir.  
  
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
  
 Ao definir um fluxo de trabalho em código, as atividades de expressão podem ser usadas. O exemplo a seguir mostra o uso de uma combinação de atividades do operador para adicionar três números.  
  
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
  
 O mesmo fluxo de trabalho pode ser expresso de modo mais compacto usando expressões lambda C#, conforme mostrado no exemplo a seguir.  
  
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
  
 O fluxo de trabalho também pode ser expresso usando atividades de expressão do Visual Basic, conforme mostrado no exemplo a seguir.  
  
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
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a>Estendendo expressões disponíveis com atividades da expressão personalizadas  
 As expressões no [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] são extensível permitindo atividades adicionais da expressão a serem criadas. O exemplo a seguir mostra uma atividade que retorna uma soma de três valores inteiros.  
  
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
  
 Com essa nova atividade, você pode reescrever o fluxo de trabalho anterior que adicionou três valores conforme mostrado no exemplo a seguir.  
  
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
  
 Para obter mais informações sobre como usar expressões no código, consulte [criação de fluxos de trabalho, atividades e expressões usando / código](authoring-workflows-activities-and-expressions-using-imperative-code.md).
