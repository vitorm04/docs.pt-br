---
title: "Implementando lógica de negócios (LINQ te o SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d905f34c29fbd8a15cb8225a4a547490a5c14efd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="implementing-business-logic-linq-to-sql"></a>Implementando lógica de negócios (LINQ te o SQL)
O termo “lógica de negócios” neste tópico faz referência a todas as regras personalizadas ou testes de validação que você aplica a dados antes de eles serem inseridos, atualizados ou excluídos do banco de dados. A lógica de negócios às vezes também é conhecida como "regras de negócio" ou "lógica de domínio". Em aplicativos de n camadas ela normalmente é criada como uma camada lógica para que possa ser modificada independentemente da camada de apresentação ou da camada de acesso a dados. A lógica de negócios pode ser chamada pela camada de acesso a dados antes ou depois de qualquer atualização, inserção ou exclusão de dados no banco de dados.  
  
 A lógica de negócios pode ser tão simples quanto uma validação de esquema para garantir que o tipo do campo seja compatível com o tipo da coluna da tabela. Ou pode consistir em um conjunto de objetos que interagem de maneiras arbitrariamente complexas. As regras podem ser implementadas como procedimentos armazenados no banco de dados ou como objetos na memória. No entanto, a lógica de negócios é implementada, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] permite que você use classes parciais e métodos parciais para separar a lógica de negócios do código de acesso a dados.  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a>Como o LINQ to SQL chama sua lógica de negócios  
 Quando você gera uma classe de entidade em tempo de design, manualmente ou utilizando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou o SQLMetal, ela é definida como uma classe parcial. Isso significa que, em um arquivo de código separado, você pode definir outra parte da classe de entidade que contém a lógica de negócios personalizada. Em tempo de compilação, as duas partes são mescladas em uma única classe. Porém, se você precisar regenerar as classes de entidade usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou SQLMetal, poderá fazê-lo e sua parte da classe não será modificado.  
  
 As classes parciais que definem entidades e o <xref:System.Data.Linq.DataContext> contêm métodos parciais. Esses são os pontos de extensibilidade que você pode usar para aplicar sua lógica de negócios antes e depois de qualquer atualização, inserção ou exclusão de uma entidade ou propriedade de entidade. Os métodos parciais podem ser considerados como eventos em tempo de compilação. O gerador de código define uma assinatura do método e chama os métodos nos acessadores de propriedade get e set, o construtor de `DataContext` e, em alguns casos o código em segundo plano quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado. Entretanto, se você não implementar um método parcial específico, todas as referências a ele e a definição serão removidos em tempo de compilação.  
  
 Na definição da implementação que você escreve no arquivo de código separado, você pode executar qualquer lógica personalizada que seja necessária. Você pode usar a classe parcial própria como a camada de domínio ou chamar da definição de sua implementação do método parcial em um objeto ou objetos separados. De qualquer forma, sua lógica de negócios é corretamente separada do seu código de acesso a dados e do seu código da camada de apresentação.  
  
## <a name="a-closer-look-at-the-extensibility-points"></a>Uma visão mais profunda dos pontos de extensibilidade  
 O exemplo a seguir mostra parte do código gerado pelo [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para o `DataContext` classe que tem duas tabelas: `Customers` e `Orders`. Observe que os métodos Insert, Update e Delete são definidos para cada tabela da classe.  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 Se você implementar os métodos Insert, Update e Delete em sua classe parcial, o tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] os chamará em vez de seus próprios métodos padrão quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> for chamado. Isso permite que você substitua o comportamento padrão para operações de criação/leitura/atualização/exclusão. Para obter mais informações, consulte [passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).  
  
 O método `OnCreated` é chamado no construtor da classe.  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 As classes de entidade têm três métodos que são chamados pelo tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em que a entidade é criada, carregada, e validada (quando `SubmitChanges` é chamado). As classes de entidade também tem dois métodos parciais para cada propriedade, que é chamado antes que a propriedade estiver definida e um que são chamados depois. O exemplo de código a seguir mostra alguns dos métodos gerados para a classe `Customer`:  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 Os métodos são chamados no acessador de definição da propriedade conforme mostrado no exemplo a seguir para a propriedade `CustomerID`:  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 Na sua parte da classe, você escreve uma definição de implementação do método. Em [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)], depois de digitar `partial` você verá o IntelliSense para as definições de método em outra parte da classe.  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer   
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 Para obter mais informações sobre como adicionar lógica de negócios a seu aplicativo usando métodos parciais, consulte os tópicos a seguir:  
  
 [Como adicionar validação a classes de entidade](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 [Passo a passo: Adicionando validação a Classes de entidade](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)  
  
## <a name="see-also"></a>Consulte também  
 [Classes e métodos parciais](~/docs/csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)  
 [Métodos Parciais](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)  
 [Ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)  
 [SqlMetal.exe (Ferramenta de Geração de Código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
