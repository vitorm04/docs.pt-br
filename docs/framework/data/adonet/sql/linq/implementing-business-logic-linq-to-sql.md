---
title: Implementando lógica de negócios (LINQ te o SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3dcc6f763acfff076bb03076a17e3a8f8916267c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097246"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="5666f-102">Implementando lógica de negócios (LINQ te o SQL)</span><span class="sxs-lookup"><span data-stu-id="5666f-102">Implementing Business Logic (LINQ to SQL)</span></span>
<span data-ttu-id="5666f-103">O termo “lógica de negócios” neste tópico faz referência a todas as regras personalizadas ou testes de validação que você aplica a dados antes de eles serem inseridos, atualizados ou excluídos do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5666f-103">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="5666f-104">A lógica de negócios às vezes também é conhecida como "regras de negócio" ou "lógica de domínio".</span><span class="sxs-lookup"><span data-stu-id="5666f-104">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="5666f-105">Em aplicativos de n camadas ela normalmente é criada como uma camada lógica para que possa ser modificada independentemente da camada de apresentação ou da camada de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="5666f-105">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="5666f-106">A lógica de negócios pode ser chamada pela camada de acesso a dados antes ou depois de qualquer atualização, inserção ou exclusão de dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5666f-106">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="5666f-107">A lógica de negócios pode ser tão simples quanto uma validação de esquema para garantir que o tipo do campo seja compatível com o tipo da coluna da tabela.</span><span class="sxs-lookup"><span data-stu-id="5666f-107">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="5666f-108">Ou pode consistir em um conjunto de objetos que interagem de maneiras arbitrariamente complexas.</span><span class="sxs-lookup"><span data-stu-id="5666f-108">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="5666f-109">As regras podem ser implementadas como procedimentos armazenados no banco de dados ou como objetos na memória.</span><span class="sxs-lookup"><span data-stu-id="5666f-109">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="5666f-110">No entanto, a lógica de negócios é implementada, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] permite usar classes parciais e métodos parciais para separar a lógica de negócios do código de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="5666f-110">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="5666f-111">Como o LINQ to SQL chama sua lógica de negócios</span><span class="sxs-lookup"><span data-stu-id="5666f-111">How LINQ to SQL Invokes Your Business Logic</span></span>  
 <span data-ttu-id="5666f-112">Quando você gera uma classe de entidade em tempo de design, manualmente ou utilizando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou o SQLMetal, ela é definida como uma classe parcial.</span><span class="sxs-lookup"><span data-stu-id="5666f-112">When you generate an entity class at design time, either manually or by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="5666f-113">Isso significa que, em um arquivo de código separado, você pode definir outra parte da classe de entidade que contém a lógica de negócios personalizada.</span><span class="sxs-lookup"><span data-stu-id="5666f-113">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="5666f-114">Em tempo de compilação, as duas partes são mescladas em uma única classe.</span><span class="sxs-lookup"><span data-stu-id="5666f-114">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="5666f-115">Mas se você precisar regenerar as classes de entidade usando o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ou SQLMetal, você poderá fazer isso e sua parte da classe não será modificado.</span><span class="sxs-lookup"><span data-stu-id="5666f-115">But if you have to regenerate your entity classes by using the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="5666f-116">As classes parciais que definem entidades e o <xref:System.Data.Linq.DataContext> contêm métodos parciais.</span><span class="sxs-lookup"><span data-stu-id="5666f-116">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="5666f-117">Esses são os pontos de extensibilidade que você pode usar para aplicar sua lógica de negócios antes e depois de qualquer atualização, inserção ou exclusão de uma entidade ou propriedade de entidade.</span><span class="sxs-lookup"><span data-stu-id="5666f-117">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="5666f-118">Os métodos parciais podem ser considerados como eventos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="5666f-118">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="5666f-119">O gerador de código define uma assinatura do método e chama os métodos nos acessadores de propriedade get e set, o construtor de `DataContext` e, em alguns casos o código em segundo plano quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="5666f-119">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="5666f-120">Entretanto, se você não implementar um método parcial específico, todas as referências a ele e a definição serão removidos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="5666f-120">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="5666f-121">Na definição da implementação que você escreve no arquivo de código separado, você pode executar qualquer lógica personalizada que seja necessária.</span><span class="sxs-lookup"><span data-stu-id="5666f-121">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="5666f-122">Você pode usar a classe parcial própria como a camada de domínio ou chamar da definição de sua implementação do método parcial em um objeto ou objetos separados.</span><span class="sxs-lookup"><span data-stu-id="5666f-122">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="5666f-123">De qualquer forma, sua lógica de negócios é corretamente separada do seu código de acesso a dados e do seu código da camada de apresentação.</span><span class="sxs-lookup"><span data-stu-id="5666f-123">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="5666f-124">Uma visão mais profunda dos pontos de extensibilidade</span><span class="sxs-lookup"><span data-stu-id="5666f-124">A Closer Look at the Extensibility Points</span></span>  
 <span data-ttu-id="5666f-125">O exemplo a seguir mostra parte do código gerado pelo [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para o `DataContext` classe que tem duas tabelas: `Customers` e `Orders`.</span><span class="sxs-lookup"><span data-stu-id="5666f-125">The following example shows part of the code generated by the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="5666f-126">Observe que os métodos Insert, Update e Delete são definidos para cada tabela da classe.</span><span class="sxs-lookup"><span data-stu-id="5666f-126">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
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
  
 <span data-ttu-id="5666f-127">Se você implementar os métodos Insert, Update e Delete em sua classe parcial, o tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] os chamará em vez de seus próprios métodos padrão quando <xref:System.Data.Linq.DataContext.SubmitChanges%2A> for chamado.</span><span class="sxs-lookup"><span data-stu-id="5666f-127">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="5666f-128">Isso permite que você substitua o comportamento padrão para operações de criação/leitura/atualização/exclusão.</span><span class="sxs-lookup"><span data-stu-id="5666f-128">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="5666f-129">Para obter mais informações, confira [Passo a passo: Personalizando a inserção, atualização e exclusão de comportamento de classes de entidade](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span><span class="sxs-lookup"><span data-stu-id="5666f-129">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="5666f-130">O método `OnCreated` é chamado no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="5666f-130">The `OnCreated` method is called in the class constructor.</span></span>  
  
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
  
 <span data-ttu-id="5666f-131">As classes de entidade têm três métodos que são chamados pelo tempo de execução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] em que a entidade é criada, carregada, e validada (quando `SubmitChanges` é chamado).</span><span class="sxs-lookup"><span data-stu-id="5666f-131">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="5666f-132">As classes de entidade também têm dois métodos parciais para cada propriedade, que é chamado antes que a propriedade é definida e um que são chamados depois.</span><span class="sxs-lookup"><span data-stu-id="5666f-132">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="5666f-133">O exemplo de código a seguir mostra alguns dos métodos gerados para a classe `Customer`:</span><span class="sxs-lookup"><span data-stu-id="5666f-133">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
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
  
 <span data-ttu-id="5666f-134">Os métodos são chamados no acessador de definição da propriedade conforme mostrado no exemplo a seguir para a propriedade `CustomerID`:</span><span class="sxs-lookup"><span data-stu-id="5666f-134">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
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
  
 <span data-ttu-id="5666f-135">Na sua parte da classe, você escreve uma definição de implementação do método.</span><span class="sxs-lookup"><span data-stu-id="5666f-135">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="5666f-136">No Visual Studio, depois de digitar `partial` você verá o IntelliSense para as definições do método na outra parte da classe.</span><span class="sxs-lookup"><span data-stu-id="5666f-136">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
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
  
 <span data-ttu-id="5666f-137">Para obter mais informações sobre como adicionar lógica de negócios a seu aplicativo usando métodos parciais, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="5666f-137">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="5666f-138">Como: Adicionar validação a classes de entidade</span><span class="sxs-lookup"><span data-stu-id="5666f-138">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="5666f-139">Passo a passo: Personalizando o comportamento de inserção, atualização e exclusão de classes de entidade</span><span class="sxs-lookup"><span data-stu-id="5666f-139">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="5666f-140">[Passo a passo: Adicionando validação a Classes de entidade](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5666f-140">[Walkthrough: Adding Validation to Entity Classes](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5666f-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5666f-141">See also</span></span>

- [<span data-ttu-id="5666f-142">Classes e métodos parciais</span><span class="sxs-lookup"><span data-stu-id="5666f-142">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="5666f-143">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="5666f-143">Partial Methods</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- [<span data-ttu-id="5666f-144">Ferramentas LINQ to SQL no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5666f-144">LINQ to SQL Tools in Visual Studio</span></span>](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [<span data-ttu-id="5666f-145">SqlMetal.exe (Ferramenta de Geração de Código)</span><span class="sxs-lookup"><span data-stu-id="5666f-145">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
