---
title: "Uso de atividade de opção com tipos personalizados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8a4418c582d00f1163305ce5d63c63c198dbc30
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="2c06a-102">Uso de atividade de opção com tipos personalizados</span><span class="sxs-lookup"><span data-stu-id="2c06a-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="2c06a-103">Este exemplo descreve como habilitar um <!--zz <xref:System.Activities. Statements.Switch`1>--> `xref:System.Activities` Statements.Switch`1?qualifyHint=False&autoUpgrade=True activity to evaluate a user-defined complex type at runtime. In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable. Traditionally, a \`alternar ' instrução opera em uma expressão que pode ser avaliada estaticamente.</span><span class="sxs-lookup"><span data-stu-id="2c06a-103">This sample describes how to enable a <!--zz <xref:System.Activities. Statements.Switch`1>--> `xref:System.Activities` Statements.Switch`1?qualifyHint=False&autoUpgrade=True activity to evaluate a user-defined complex type at runtime. In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable. Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="2c06a-104">Por exemplo, em C# isso significa que apenas os tipos primitivos, como <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, e tipos de enumeração são suportados.</span><span class="sxs-lookup"><span data-stu-id="2c06a-104">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="2c06a-105">Para habilitar a exibição em uma classe personalizada, a lógica deve ser implementada para avaliar valores do tipo complexo personalizado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2c06a-105">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="2c06a-106">Este exemplo demonstra como habilitar a exibição em um tipo complexo personalizado chamado `Person`.</span><span class="sxs-lookup"><span data-stu-id="2c06a-106">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="2c06a-107">Na classe personalizada `Person`, um atributo de <xref:System.ComponentModel.TypeConverter> é declarado com o nome de <xref:System.ComponentModel.TypeConverter>personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c06a-107">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="2c06a-108">Na classe personalizada `Person`, classes de <xref:System.Object.Equals%2A> e de <xref:System.Object.GetHashCode%2A> são substituídas.</span><span class="sxs-lookup"><span data-stu-id="2c06a-108">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="2c06a-109">Uma classe de <xref:System.ComponentModel.TypeConverter> personalizado é implementada que executa a conversão de uma instância da classe personalizado em uma cadeia de caracteres e uma cadeia de caracteres a uma instância de uma classe personalizada.</span><span class="sxs-lookup"><span data-stu-id="2c06a-109">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="2c06a-110">Os seguintes arquivos são incluídos neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c06a-110">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="2c06a-111">**Person.CS**: define o `Person` classe.</span><span class="sxs-lookup"><span data-stu-id="2c06a-111">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="2c06a-112">**PersonConverter.cs**: O conversor de tipo para o `Person` classe.</span><span class="sxs-lookup"><span data-stu-id="2c06a-112">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="2c06a-113">**Sequence.XAML**: um fluxo de trabalho que muda a `Person` tipo.</span><span class="sxs-lookup"><span data-stu-id="2c06a-113">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="2c06a-114">**Program.CS**: A função principal que executa o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2c06a-114">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2c06a-115">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2c06a-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="2c06a-116">Carregamento Switch.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c06a-116">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="2c06a-117">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="2c06a-117">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="2c06a-118">O pressionar o CTRL + F5 para executar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="2c06a-118">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2c06a-119">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2c06a-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c06a-120">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2c06a-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2c06a-121">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="2c06a-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c06a-122">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2c06a-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="2c06a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c06a-123">See Also</span></span>  
 [<span data-ttu-id="2c06a-124">Biblioteca interno de atividades</span><span class="sxs-lookup"><span data-stu-id="2c06a-124">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
