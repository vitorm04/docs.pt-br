---
title: Uso de atividade de opção com tipos personalizados
ms.date: 03/30/2017
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
ms.openlocfilehash: b24a03573b31f3fb1c34d4aa6e03bc11f5b25455
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535433"
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Uso de atividade de opção com tipos personalizados
Este exemplo descreve como ativar uma atividade de <xref:System.Activities.Statements.Switch%601> para avaliar um tipo complexo definido pelo usuário em tempo de execução. Em linguagens de programação procedurais mais tradicionais, um [alternar](https://go.microsoft.com/fwlink/?LinkId=180521) instrução seleciona uma lógica de execução com base na avaliação condicional de uma variável. Tradicionalmente, uma instrução de `switch` opera em uma expressão que estaticamente pode ser avaliada. Por exemplo, em C# isso significa que apenas os tipos primitivos, como <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, e tipos de enumeração são suportados.  
  
 Para habilitar a exibição em uma classe personalizada, a lógica deve ser implementada para avaliar valores do tipo complexo personalizado em tempo de execução. Este exemplo demonstra como habilitar a exibição em um tipo complexo personalizado chamado `Person`.  
  
-   Na classe personalizada `Person`, um atributo de <xref:System.ComponentModel.TypeConverter> é declarado com o nome de <xref:System.ComponentModel.TypeConverter>personalizado.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Na classe personalizada `Person`, classes de <xref:System.Object.Equals%2A> e de <xref:System.Object.GetHashCode%2A> são substituídas.  
  
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
  
-   Uma classe de <xref:System.ComponentModel.TypeConverter> personalizado é implementada que executa a conversão de uma instância da classe personalizado em uma cadeia de caracteres e uma cadeia de caracteres a uma instância de uma classe personalizada.  
  
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
  
 Os seguintes arquivos são incluídos neste exemplo:  
  
-   **Person.CS**: define o `Person` classe.  
  
-   **1&gt;personconverter.CS&lt;1**: O conversor de tipo para o `Person` classe.  
  
-   **1&gt;Sequence.XAML&lt;1**: um fluxo de trabalho que alterne sobre o `Person` tipo.  
  
-   **Program.CS**: A função principal que executa o fluxo de trabalho.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregamento Switch.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  O pressionar o CTRL + F5 para executar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Consulte também  
 [Biblioteca interno de atividades](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)
