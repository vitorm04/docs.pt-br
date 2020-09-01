---
title: Diretrizes de segurança do conjunto de tabela e DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 4fe8a062c762cc70d33243e3443aa9bf55635f98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137611"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="efe61-102">Diretrizes de segurança do conjunto de tabela e DataTable</span><span class="sxs-lookup"><span data-stu-id="efe61-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="efe61-103">Este artigo aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="efe61-103">This article applies to:</span></span>

* <span data-ttu-id="efe61-104">.NET Framework (todas as versões)</span><span class="sxs-lookup"><span data-stu-id="efe61-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="efe61-105">.NET Core e posterior</span><span class="sxs-lookup"><span data-stu-id="efe61-105">.NET Core and later</span></span>
* <span data-ttu-id="efe61-106">.NET 5,0 e posterior</span><span class="sxs-lookup"><span data-stu-id="efe61-106">.NET 5.0 and later</span></span>

<span data-ttu-id="efe61-107">Os tipos [DataSet](/dotnet/api/system.data.dataset) e [DataTable](/dotnet/api/system.data.datatable) são componentes .net herdados que permitem a representação de conjuntos de dados como objetos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="efe61-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="efe61-108">Esses componentes foram introduzidos no .NET 1,0 como parte da infraestrutura original do [ADO.net](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span><span class="sxs-lookup"><span data-stu-id="efe61-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="efe61-109">Sua meta era fornecer uma exibição gerenciada sobre um conjunto de dados relacionais, abstraindo se a fonte subjacente dos dados era XML, SQL ou outra tecnologia.</span><span class="sxs-lookup"><span data-stu-id="efe61-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="efe61-110">Para obter mais informações sobre ADO.NET, incluindo paradigmas de exibição de dados mais modernos, consulte [a documentação do ADO.net](/dotnet/framework/data/adonet/).</span><span class="sxs-lookup"><span data-stu-id="efe61-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="efe61-111">Restrições padrão ao desserializar um DataSet ou DataTable de XML</span><span class="sxs-lookup"><span data-stu-id="efe61-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="efe61-112">Em todas as versões com suporte do .NET Framework, .NET Core e .NET, `DataSet` e `DataTable` Coloque as seguintes restrições sobre quais tipos de objetos podem estar presentes nos dados desserializados.</span><span class="sxs-lookup"><span data-stu-id="efe61-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="efe61-113">Por padrão, essa lista é restrita a:</span><span class="sxs-lookup"><span data-stu-id="efe61-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="efe61-114">Primitivas e equivalentes primitivos:,,,,,, `bool` `char` `sbyte` `byte` `short` `ushort` `int` , `uint` ,,,,,,,,,,,, `long` `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` , `SqlByte` , `SqlBytes` ,,,, `SqlChars` ,,,,,, `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` e `SqlString` .</span><span class="sxs-lookup"><span data-stu-id="efe61-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="efe61-115">Não primitivos comumente usados: `Type` , `Uri` e `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="efe61-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="efe61-116">Tipos de _sistema. Drawing_ usados com frequência: `Color` ,,,, `Point` `PointF` `Rectangle` `RectangleF` , `Size` e `SizeF` .</span><span class="sxs-lookup"><span data-stu-id="efe61-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="efe61-117">`Enum` digita.</span><span class="sxs-lookup"><span data-stu-id="efe61-117">`Enum` types.</span></span>
* <span data-ttu-id="efe61-118">Matrizes e listas dos tipos acima.</span><span class="sxs-lookup"><span data-stu-id="efe61-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="efe61-119">Se os dados XML de entrada contiverem um objeto cujo tipo não está nesta lista:</span><span class="sxs-lookup"><span data-stu-id="efe61-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="efe61-120">Uma exceção é lançada com a mensagem e o rastreamento de pilha a seguir.</span><span class="sxs-lookup"><span data-stu-id="efe61-120">An exception is thrown with the following message and stack trace.</span></span>  
<span data-ttu-id="efe61-121">Mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="efe61-121">Error Message:</span></span>  
<span data-ttu-id="efe61-122">System. InvalidOperationException: tipo ' \<Type Name\> , Version = \<n.n.n.n\> , Culture = \<culture\> , PublicKeyToken = \<token value\> ' não é permitido aqui.</span><span class="sxs-lookup"><span data-stu-id="efe61-122">System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="efe61-123">Consulte [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="efe61-123">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>  
<span data-ttu-id="efe61-124">Rastreamento de pilha:</span><span class="sxs-lookup"><span data-stu-id="efe61-124">Stack Trace:</span></span>  
<span data-ttu-id="efe61-125">em System. Data. TypeLimiter. EnsureTypeIsAllowed (tipo Type, TypeLimiter capturedLimiter)</span><span class="sxs-lookup"><span data-stu-id="efe61-125">at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter)</span></span>  
<span data-ttu-id="efe61-126">em System. Data. DataColumn. UpdateColumnType (tipo Type, o storagetype typeCode)</span><span class="sxs-lookup"><span data-stu-id="efe61-126">at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode)</span></span>  
<span data-ttu-id="efe61-127">em System. Data. DataColumn. set_DataType (valor de tipo)</span><span class="sxs-lookup"><span data-stu-id="efe61-127">at System.Data.DataColumn.set_DataType(Type value)</span></span>  

* <span data-ttu-id="efe61-128">A operação de desserialização falha.</span><span class="sxs-lookup"><span data-stu-id="efe61-128">The deserialization operation fails.</span></span>

<span data-ttu-id="efe61-129">Ao carregar XML em uma `DataSet` instância ou existente `DataTable` , as definições de coluna existentes também são levadas em conta.</span><span class="sxs-lookup"><span data-stu-id="efe61-129">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="efe61-130">Se a tabela já contiver uma definição de coluna de um tipo personalizado, esse tipo será adicionado temporariamente à lista de permissões para a duração da operação de desserialização de XML.</span><span class="sxs-lookup"><span data-stu-id="efe61-130">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="efe61-131">Depois que você adicionar colunas a um `DataTable` , o `ReadXml` não lerá o esquema do XML e, se o esquema não corresponder, ele também não será lido nos registros, portanto, você precisará adicionar todas as colunas por conta própria para usar esse método.</span><span class="sxs-lookup"><span data-stu-id="efe61-131">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="efe61-132">As restrições de tipo de objeto também se aplicam ao usar `XmlSerializer` para desserializar uma instância do `DataSet` ou `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="efe61-132">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="efe61-133">No entanto, eles não podem se aplicar ao usar `BinaryFormatter` o para desserializar uma instância do `DataSet` ou `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="efe61-133">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="efe61-134">As restrições de tipo de objeto não se aplicam ao usar `DataAdapter.Fill` o, como quando uma `DataTable` instância é populada diretamente de um banco de dados sem usar as APIs de desserialização de XML.</span><span class="sxs-lookup"><span data-stu-id="efe61-134">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="efe61-135">Estender a lista de tipos permitidos</span><span class="sxs-lookup"><span data-stu-id="efe61-135">Extend the list of allowed types</span></span>

<span data-ttu-id="efe61-136">Um aplicativo pode estender a lista de tipos permitidos para incluir tipos personalizados, além dos tipos internos listados acima.</span><span class="sxs-lookup"><span data-stu-id="efe61-136">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="efe61-137">Se estiver estendendo a lista de tipos permitidos, a alteração afetará _todas as_ `DataSet` `DataTable` instâncias e no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efe61-137">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="efe61-138">Os tipos não podem ser removidos da lista de tipos permitidos internos.</span><span class="sxs-lookup"><span data-stu-id="efe61-138">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="efe61-139">Estender por meio da configuração (.NET Framework 4,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="efe61-139">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="efe61-140">_App.config_ pode ser usado para estender a lista de tipos permitidos.</span><span class="sxs-lookup"><span data-stu-id="efe61-140">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="efe61-141">Para estender a lista de tipos permitidos:</span><span class="sxs-lookup"><span data-stu-id="efe61-141">To extend the allowed types list:</span></span>

* <span data-ttu-id="efe61-142">Use o `<configSections>` elemento para adicionar uma referência à seção de configuração _System. Data_ .</span><span class="sxs-lookup"><span data-stu-id="efe61-142">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="efe61-143">Use `<system.data.dataset.serialization>` / `<allowedTypes>` para especificar tipos adicionais.</span><span class="sxs-lookup"><span data-stu-id="efe61-143">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="efe61-144">Cada `<add>` elemento deve especificar apenas um tipo usando seu nome de tipo qualificado de assembly.</span><span class="sxs-lookup"><span data-stu-id="efe61-144">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="efe61-145">Para adicionar tipos adicionais à lista de tipos permitidos, use vários `<add>` elementos.</span><span class="sxs-lookup"><span data-stu-id="efe61-145">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="efe61-146">O exemplo a seguir mostra a extensão da lista de tipos permitidos adicionando o tipo personalizado `Fabrikam.CustomType` .</span><span class="sxs-lookup"><span data-stu-id="efe61-146">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="efe61-147">Para recuperar o nome qualificado do assembly de um tipo, use a propriedade [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , conforme demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="efe61-147">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="efe61-148">Estender por meio da configuração (.NET Framework 2,0-3,5)</span><span class="sxs-lookup"><span data-stu-id="efe61-148">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="efe61-149">Se seu aplicativo tiver como destino .NET Framework 2,0 ou 3,5, você ainda poderá usar o mecanismo de _App.config_ acima para estender a lista de tipos permitidos.</span><span class="sxs-lookup"><span data-stu-id="efe61-149">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="efe61-150">No entanto, seu `<configSections>` elemento parecerá um pouco diferente, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-150">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="efe61-151">Estender programaticamente (.NET Framework, .NET Core, .NET 5.0 +)</span><span class="sxs-lookup"><span data-stu-id="efe61-151">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="efe61-152">A lista de tipos permitidos também pode ser estendida programaticamente usando [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) com a chave conhecida _System. Data. DataSetDefaultAllowedTypes_, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="efe61-152">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="efe61-153">Se estiver usando o mecanismo de extensão, o valor associado à chave _System. Data. DataSetDefaultAllowedTypes_ deverá ser do tipo `Type[]` .</span><span class="sxs-lookup"><span data-stu-id="efe61-153">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="efe61-154">Em .NET Framework, a lista de tipos permitidos pode ser estendida com _App.config_ e `AppDomain.SetData` .</span><span class="sxs-lookup"><span data-stu-id="efe61-154">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="efe61-155">Nesse caso, `DataSet` e `DataTable` permitirá que um objeto seja desserializado como parte dos dados se seu tipo estiver presente em qualquer uma das listas.</span><span class="sxs-lookup"><span data-stu-id="efe61-155">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="efe61-156">Executar um aplicativo no modo de auditoria (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="efe61-156">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="efe61-157">No .NET Framework, `DataSet` e `DataTable` fornecem um recurso de modo de auditoria.</span><span class="sxs-lookup"><span data-stu-id="efe61-157">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="efe61-158">Quando o modo de auditoria está habilitado `DataSet` e `DataTable` compara os tipos de objetos de entrada com a lista de tipos permitidos.</span><span class="sxs-lookup"><span data-stu-id="efe61-158">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="efe61-159">No entanto, se um objeto cujo tipo não é permitido for visto, uma exceção **não** será lançada.</span><span class="sxs-lookup"><span data-stu-id="efe61-159">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="efe61-160">Em vez disso, `DataSet` e `DataTable` notifique as instâncias anexadas `TraceListener` que um tipo suspeito está presente, permitindo que o `TraceListener` Registre essas informações.</span><span class="sxs-lookup"><span data-stu-id="efe61-160">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="efe61-161">Nenhuma exceção é lançada e a operação de desserialização continua.</span><span class="sxs-lookup"><span data-stu-id="efe61-161">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="efe61-162">A execução de um aplicativo no "modo de auditoria" deve ser apenas uma medida temporária usada para teste.</span><span class="sxs-lookup"><span data-stu-id="efe61-162">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="efe61-163">Quando o modo de auditoria está habilitado `DataSet` e `DataTable` não impõe restrições de tipo, que podem introduzir uma brecha de segurança dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efe61-163">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="efe61-164">Para obter mais informações, consulte as seções intituladas [removendo todas as restrições de tipo](#ratr) e [segurança em relação à entrada não confiável](#swr).</span><span class="sxs-lookup"><span data-stu-id="efe61-164">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="efe61-165">O modo de auditoria pode ser habilitado por meio do _App.config_:</span><span class="sxs-lookup"><span data-stu-id="efe61-165">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="efe61-166">Consulte a seção [ampliando a configuração](#etc) deste documento para obter informações sobre o valor adequado a ser colocado para o `<configSections>` elemento.</span><span class="sxs-lookup"><span data-stu-id="efe61-166">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="efe61-167">Use `<allowedTypes auditOnly="true">` para habilitar o modo de auditoria, conforme mostrado na marcação a seguir.</span><span class="sxs-lookup"><span data-stu-id="efe61-167">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="efe61-168">Depois que o modo de auditoria estiver habilitado, você poderá usar _App.config_ para conectar seu preferido `TraceListener` ao `DataSet` `TraceSource.` nome da origem de rastreamento interna é _System. Data. DataSet_.</span><span class="sxs-lookup"><span data-stu-id="efe61-168">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="efe61-169">O exemplo a seguir demonstra a gravação de eventos de rastreamento no console _e_ em um arquivo de log no disco.</span><span class="sxs-lookup"><span data-stu-id="efe61-169">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="efe61-170">Para obter mais informações `TraceSource` sobre `TraceListener` o e o, consulte o documento [como: usar rastreamento e filtros com ouvintes de rastreamento](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="efe61-170">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="efe61-171">A execução de um aplicativo no modo de auditoria não está disponível no .NET Core ou no .NET 5,0 e posterior.</span><span class="sxs-lookup"><span data-stu-id="efe61-171">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="efe61-172">Remover todas as restrições de tipo</span><span class="sxs-lookup"><span data-stu-id="efe61-172">Remove all type restrictions</span></span>

<span data-ttu-id="efe61-173">Se um aplicativo deve remover todas as restrições de limitação de tipo de `DataSet` e `DataTable` :</span><span class="sxs-lookup"><span data-stu-id="efe61-173">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="efe61-174">Há várias opções para suprimir as restrições de limitação de tipo.</span><span class="sxs-lookup"><span data-stu-id="efe61-174">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="efe61-175">As opções disponíveis dependem da estrutura de destino do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efe61-175">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="efe61-176">A remoção de todas as restrições de tipo pode introduzir uma brecha de segurança dentro do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="efe61-176">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="efe61-177">Ao usar esse mecanismo, verifique se o aplicativo **não** usa `DataSet` ou `DataTable` para ler a entrada não confiável.</span><span class="sxs-lookup"><span data-stu-id="efe61-177">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="efe61-178">Para obter mais informações, consulte [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) e a seção a seguir intitulada [segurança em relação à entrada não confiável](#swr).</span><span class="sxs-lookup"><span data-stu-id="efe61-178">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="efe61-179">Por meio da configuração do AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 e posterior, .NET 5,0 e posterior)</span><span class="sxs-lookup"><span data-stu-id="efe61-179">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="efe61-180">A `AppContext` opção, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , quando definida como `true` Remove todas as restrições de limitação de tipo de `DataSet` e `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="efe61-180">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="efe61-181">No .NET Framework, essa opção pode ser habilitada via _App.config_, conforme mostrado na seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="efe61-181">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="efe61-182">No ASP.NET, o `<AppContextSwitchOverrides>` elemento não está disponível.</span><span class="sxs-lookup"><span data-stu-id="efe61-182">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="efe61-183">Em vez disso, a opção pode ser habilitada por meio de _Web.config_, conforme mostrado na seguinte configuração:</span><span class="sxs-lookup"><span data-stu-id="efe61-183">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="efe61-184">Para obter mais informações, consulte o [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="efe61-184">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="efe61-185">No .NET Core, no .NET 5 e no ASP.NET Core, essa configuração é controlada por _runtimeconfig.jsem_, conforme mostrado no JSON a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-185">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="efe61-186">Para obter mais informações, consulte ["definições de configuração de tempo de execução do .NET Core"](/dotnet/core/run-time-config/).</span><span class="sxs-lookup"><span data-stu-id="efe61-186">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="efe61-187">`AllowArbitraryDataSetTypeInstantiation` também pode ser definido programaticamente via [AppContext. setswitch](/dotnet/api/system.appcontext.setswitch) em vez de usar um arquivo de configuração, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-187">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="efe61-188">Se você escolher a abordagem programática anterior, a chamada para `AppContext.SetSwitch` deverá ocorrer no início da inicialização dos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="efe61-188">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="efe61-189">Por meio do registro em todo o computador (.NET Framework 2,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="efe61-189">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="efe61-190">Se `AppContext` não estiver disponível, as verificações de limitação de tipo poderão ser desabilitadas com o registro do Windows:</span><span class="sxs-lookup"><span data-stu-id="efe61-190">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="efe61-191">Um administrador deve configurar o registro.</span><span class="sxs-lookup"><span data-stu-id="efe61-191">An administrator must configure the registry.</span></span>
* <span data-ttu-id="efe61-192">O uso do registro é uma alteração em todo o computador e afetará _todos os_ aplicativos em execução no computador.</span><span class="sxs-lookup"><span data-stu-id="efe61-192">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="efe61-193">Tipo</span><span class="sxs-lookup"><span data-stu-id="efe61-193">Type</span></span>  |  <span data-ttu-id="efe61-194">Valor</span><span class="sxs-lookup"><span data-stu-id="efe61-194">Value</span></span> |
|---|---|
| <span data-ttu-id="efe61-195">**Chave do Registro**</span><span class="sxs-lookup"><span data-stu-id="efe61-195">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="efe61-196">**Nome do valor**</span><span class="sxs-lookup"><span data-stu-id="efe61-196">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="efe61-197">**Tipo de valor**</span><span class="sxs-lookup"><span data-stu-id="efe61-197">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="efe61-198">**Dados do valor**</span><span class="sxs-lookup"><span data-stu-id="efe61-198">**Value data**</span></span> | `true` |

<span data-ttu-id="efe61-199">Em um sistema operacional de 64 bits, esse valor deve ser adicionado para a chave de 64 bits (mostrada acima) e a chave 32 bits.</span><span class="sxs-lookup"><span data-stu-id="efe61-199">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="efe61-200">A chave de 32 bits está localizada em `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .</span><span class="sxs-lookup"><span data-stu-id="efe61-200">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="efe61-201">Para obter mais informações sobre como usar o registro para configurar o `AppContext` , consulte ["AppContext for Library consumidores"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span><span class="sxs-lookup"><span data-stu-id="efe61-201">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="efe61-202">Segurança em relação à entrada não confiável</span><span class="sxs-lookup"><span data-stu-id="efe61-202">Safety with regard to untrusted input</span></span>

<span data-ttu-id="efe61-203">Embora `DataSet` e `DataTable` imponham as limitações padrão nos tipos que podem estar presentes durante a desserialização de cargas XML __ `DataSet` e, `DataTable` em geral, não são seguras quando preenchidas com entrada não confiável.__</span><span class="sxs-lookup"><span data-stu-id="efe61-203">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="efe61-204">Veja a seguir uma lista de maneiras não exaustivas de que `DataSet` uma `DataTable` instância ou pode ler uma entrada não confiável.</span><span class="sxs-lookup"><span data-stu-id="efe61-204">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="efe61-205">Um `DataAdapter` faz referência a um banco de dados e o `DataAdapter.Fill` método é usado para popular um `DataSet` com o conteúdo de uma consulta de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="efe61-205">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="efe61-206">O `DataSet.ReadXml` `DataTable.ReadXml` método ou é usado para ler um arquivo XML contendo informações de coluna e linha.</span><span class="sxs-lookup"><span data-stu-id="efe61-206">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="efe61-207">Uma `DataSet` `DataTable` instância ou é serializada como parte de um ASP.net (SOAP) serviços Web ou um ponto de extremidade WCF.</span><span class="sxs-lookup"><span data-stu-id="efe61-207">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="efe61-208">Um serializador, como `XmlSerializer` é usado para desserializar `DataSet` uma `DataTable` instância ou de um fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="efe61-208">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="efe61-209">Um serializador, como `JsonConvert` é usado para desserializar `DataSet` uma `DataTable` instância ou de um fluxo JSON.</span><span class="sxs-lookup"><span data-stu-id="efe61-209">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="efe61-210">`JsonConvert` é um método no conhecidoNewtonsoft.Jsde terceiros [ na](https://www.newtonsoft.com/json) biblioteca.</span><span class="sxs-lookup"><span data-stu-id="efe61-210">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="efe61-211">Um serializador, como `BinaryFormatter` é usado para desserializar `DataSet` uma `DataTable` instância ou de um fluxo de bytes brutos.</span><span class="sxs-lookup"><span data-stu-id="efe61-211">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="efe61-212">Este documento discute considerações de segurança para os cenários anteriores.</span><span class="sxs-lookup"><span data-stu-id="efe61-212">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="efe61-213">Usar `DataAdapter.Fill` para popular um `DataSet` de uma fonte de dados não confiável</span><span class="sxs-lookup"><span data-stu-id="efe61-213">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="efe61-214">Uma `DataSet` instância pode ser populada a partir de um usando `DataAdapter` [o `DataAdapter.Fill` método](/dotnet/api/system.data.common.dataadapter.fill), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="efe61-214">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="efe61-215">(O exemplo de código acima faz parte de um exemplo maior encontrado em [Populando um conjunto de uma base de um DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span><span class="sxs-lookup"><span data-stu-id="efe61-215">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="efe61-216">A maioria dos aplicativos pode simplificar e assumir que sua camada de banco de dados é confiável.</span><span class="sxs-lookup"><span data-stu-id="efe61-216">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="efe61-217">No entanto, se você estiver no hábito de [modelar](https://www.microsoft.com/securityengineering/sdl/threatmodeling) seus aplicativos, seu modelo de ameaça poderá considerar que há um limite de confiança entre o aplicativo (cliente) e a camada de banco de dados (servidor).</span><span class="sxs-lookup"><span data-stu-id="efe61-217">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="efe61-218">O uso da [autenticação mútua](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) ou da [autenticação do AAD](/azure/azure-sql/database/authentication-aad-overview) entre o cliente e o servidor é uma maneira de ajudar a resolver os riscos associados a isso.</span><span class="sxs-lookup"><span data-stu-id="efe61-218">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="efe61-219">O restante desta seção aborda o resultado possível de um cliente que se conecta a um servidor não confiável.</span><span class="sxs-lookup"><span data-stu-id="efe61-219">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="efe61-220">As consequências de apontar um `DataAdapter` em uma fonte de dados não confiável dependem da implementação da `DataAdapter` si mesma.</span><span class="sxs-lookup"><span data-stu-id="efe61-220">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="efe61-221">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="efe61-221">SqlDataAdapter</span></span>

<span data-ttu-id="efe61-222">Para o tipo interno [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), a referência a uma fonte de dados não confiável pode resultar em um ataque de negação de serviço (dos).</span><span class="sxs-lookup"><span data-stu-id="efe61-222">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="efe61-223">O ataque DoS pode fazer com que o aplicativo fique sem resposta ou falhe.</span><span class="sxs-lookup"><span data-stu-id="efe61-223">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="efe61-224">Se um invasor puder realizar a fábrica de uma DLL junto com o aplicativo, ele também poderá conseguir a execução de código local.</span><span class="sxs-lookup"><span data-stu-id="efe61-224">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="efe61-225">Outros tipos de DataAdapter</span><span class="sxs-lookup"><span data-stu-id="efe61-225">Other DataAdapter types</span></span>

<span data-ttu-id="efe61-226">`DataAdapter`Implementações de terceiros devem fazer suas próprias avaliações sobre quais garantias de segurança eles fornecem diante de entradas não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="efe61-226">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="efe61-227">O .NET não pode garantir nenhuma garantia de segurança referente a essas implementações.</span><span class="sxs-lookup"><span data-stu-id="efe61-227">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="efe61-228">DataSet. ReadXml e DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="efe61-228">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="efe61-229">Os `DataSet.ReadXml` `DataTable.ReadXml` métodos e não são seguros quando usados com entrada não confiável.</span><span class="sxs-lookup"><span data-stu-id="efe61-229">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="efe61-230">É altamente recomendável que os consumidores considerem o uso de uma das alternativas descritas posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="efe61-230">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="efe61-231">As implementações do `DataSet.ReadXml` e `DataTable.ReadXml` foram criadas originalmente antes das vulnerabilidades de serialização eram uma categoria de ameaça bem compreendida.</span><span class="sxs-lookup"><span data-stu-id="efe61-231">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="efe61-232">Como resultado, o código não segue as práticas recomendadas de segurança atuais.</span><span class="sxs-lookup"><span data-stu-id="efe61-232">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="efe61-233">Essas APIs podem ser usadas como vetores para que os invasores executem ataques de DoS aos aplicativos Web.</span><span class="sxs-lookup"><span data-stu-id="efe61-233">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="efe61-234">Esses ataques podem tornar o serviço Web sem resposta ou resultar em um encerramento de processo inesperado.</span><span class="sxs-lookup"><span data-stu-id="efe61-234">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="efe61-235">A estrutura não fornece mitigações para essas categorias de ataque e o .NET considera esse comportamento "por design".</span><span class="sxs-lookup"><span data-stu-id="efe61-235">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="efe61-236">O .NET lançou atualizações de segurança para atenuar alguns problemas, como divulgação de informações ou execução remota de código no `DataSet.ReadXml` e no `DataTable.ReadXml` .</span><span class="sxs-lookup"><span data-stu-id="efe61-236">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="efe61-237">As atualizações de segurança do .NET podem não fornecer proteção completa contra essas categorias de ameaças.</span><span class="sxs-lookup"><span data-stu-id="efe61-237">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="efe61-238">Os consumidores devem avaliar seus cenários individuais e considerar sua exposição potencial a esses riscos.</span><span class="sxs-lookup"><span data-stu-id="efe61-238">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="efe61-239">Os consumidores devem estar cientes de que as atualizações de segurança para essas APIs podem afetar a compatibilidade de aplicativos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="efe61-239">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="efe61-240">Além disso, existe a possibilidade de que uma vulnerabilidade de romance nessas APIs seja descoberta para a qual o .NET não possa publicar de forma praticamente uma atualização de segurança.</span><span class="sxs-lookup"><span data-stu-id="efe61-240">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="efe61-241">Recomendamos que os consumidores dessas APIs sejam:</span><span class="sxs-lookup"><span data-stu-id="efe61-241">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="efe61-242">Considere usar uma das alternativas descritas posteriormente neste documento.</span><span class="sxs-lookup"><span data-stu-id="efe61-242">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="efe61-243">Execute avaliações de risco individuais em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="efe61-243">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="efe61-244">É a única responsabilidade do consumidor determinar se deve utilizar essas APIs.</span><span class="sxs-lookup"><span data-stu-id="efe61-244">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="efe61-245">Os consumidores devem avaliar quaisquer riscos de segurança, técnicos e legais, incluindo requisitos regulatórios, que possam acompanhar o uso dessas APIs.</span><span class="sxs-lookup"><span data-stu-id="efe61-245">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="efe61-246">DataSet e DataTable por meio de serviços Web ASP.NET ou WCF</span><span class="sxs-lookup"><span data-stu-id="efe61-246">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="efe61-247">É possível aceitar uma `DataSet` `DataTable` instância do ou em um serviço Web ASP.net (SOAP), conforme demonstrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-247">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="efe61-248">Uma variação sobre isso não é aceitar `DataSet` ou `DataTable` diretamente como um parâmetro, mas sim aceitá-lo como parte do gráfico de objeto SERIALIZADO em SOAP geral, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-248">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="efe61-249">Ou, usando o WCF em vez de serviços Web do ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="efe61-249">Or, using WCF instead of ASP.NET web services:</span></span>

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="efe61-250">Em todos esses casos, o modelo de ameaça e as garantias de segurança são os mesmos da [seção DataSet. ReadXml e DataTable. ReadXml](#dsrdtr).</span><span class="sxs-lookup"><span data-stu-id="efe61-250">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="efe61-251">Desserializar um DataSet ou DataTable via XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="efe61-251">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="efe61-252">Os desenvolvedores podem usar `XmlSerializer` para desserializar `DataSet` e `DataTable` instâncias, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-252">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="efe61-253">Nesses casos, o modelo de ameaça e as garantias de segurança são os mesmos da [seção DataSet. ReadXml e DataTable. ReadXml](#dsrdtr)</span><span class="sxs-lookup"><span data-stu-id="efe61-253">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="efe61-254">Desserializar um DataSet ou DataTable via JsonConvert</span><span class="sxs-lookup"><span data-stu-id="efe61-254">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="efe61-255">A popular biblioteca de Newtonsoft de terceiros [JSON.net](https://www.newtonsoft.com/json) pode ser usada para desserializar `DataSet` e `DataTable` instâncias, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="efe61-255">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="efe61-256">A desserialização de uma `DataSet` ou `DataTable` dessa maneira de um blob JSON não confiável não é segura.</span><span class="sxs-lookup"><span data-stu-id="efe61-256">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="efe61-257">Esse padrão é vulnerável a um ataque de negação de serviço.</span><span class="sxs-lookup"><span data-stu-id="efe61-257">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="efe61-258">Tal ataque poderia falhar no aplicativo ou renderizá-lo sem resposta.</span><span class="sxs-lookup"><span data-stu-id="efe61-258">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="efe61-259">A Microsoft não garante nem dá suporte à implementação de bibliotecas de terceiros, como _Newtonsoft.Jsno_.</span><span class="sxs-lookup"><span data-stu-id="efe61-259">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="efe61-260">Essas informações são fornecidas para fins de integridade e são precisas no momento da elaboração deste artigo.</span><span class="sxs-lookup"><span data-stu-id="efe61-260">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="efe61-261">Desserializar um DataSet ou DataTable via BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="efe61-261">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="efe61-262">Os desenvolvedores nunca devem usar os `BinaryFormatter` `NetDataContractSerializer` `SoapFormatter` formatadores ***inseguros*** ,, ou relacionados para desserializar uma `DataSet` `DataTable` instância do ou de uma carga não confiável:</span><span class="sxs-lookup"><span data-stu-id="efe61-262">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="efe61-263">Isso é suscetível a um ataque de execução de código remoto completo.</span><span class="sxs-lookup"><span data-stu-id="efe61-263">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="efe61-264">O uso de um personalizado `SerializationBinder` não é suficiente para evitar esse tipo de ataque.</span><span class="sxs-lookup"><span data-stu-id="efe61-264">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="efe61-265">Substituições seguras</span><span class="sxs-lookup"><span data-stu-id="efe61-265">Safe replacements</span></span>

<span data-ttu-id="efe61-266">Para aplicativos que:</span><span class="sxs-lookup"><span data-stu-id="efe61-266">For apps that either:</span></span>

* <span data-ttu-id="efe61-267">Aceite `DataSet` ou `DataTable` por meio de um ponto de extremidade SOAP. asmx ou um ponto de extremidade do WCF.</span><span class="sxs-lookup"><span data-stu-id="efe61-267">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="efe61-268">Desserializar dados não confiáveis em uma instância do `DataSet` ou do `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="efe61-268">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="efe61-269">Considere substituir o modelo de objeto para usar [Entity Framework](/ef).</span><span class="sxs-lookup"><span data-stu-id="efe61-269">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="efe61-270">Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="efe61-270">Entity Framework:</span></span>

* <span data-ttu-id="efe61-271">É uma estrutura rica, moderna e orientada a objeto que pode representar dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="efe61-271">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="efe61-272">O traz [um ecossistema diversificado](/ef/core/providers/) de provedores de banco de dados para facilitar o projeto de consultas de banco de dados por meio de seus modelos de objeto Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="efe61-272">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="efe61-273">Oferece proteções internas ao desserializar dados de fontes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="efe61-273">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="efe61-274">Para aplicativos que usam `.aspx` pontos de extremidade SOAP, considere alterar esses pontos de extremidade para usar o [WCF](/dotnet/framework/wcf/).</span><span class="sxs-lookup"><span data-stu-id="efe61-274">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="efe61-275">O WCF é uma substituição mais completa dos `.asmx` serviços da Web.</span><span class="sxs-lookup"><span data-stu-id="efe61-275">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="efe61-276">Os pontos de extremidade do WCF [podem ser expostos por meio de SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) para compatibilidade com chamadores existentes.</span><span class="sxs-lookup"><span data-stu-id="efe61-276">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="efe61-277">Analisadores de código</span><span class="sxs-lookup"><span data-stu-id="efe61-277">Code analyzers</span></span>

<span data-ttu-id="efe61-278">As regras de segurança do analisador de código, que são executadas quando o código-fonte é compilado, podem ajudar a encontrar vulnerabilidades relacionadas a esse problema de segurança em C# e Visual Basic código.</span><span class="sxs-lookup"><span data-stu-id="efe61-278">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="efe61-279">Microsoft. CodeAnalysis. FxCopAnalyzers é um pacote NuGet de analisadores de código que é distribuído no [NuGet.org](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="efe61-279">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="efe61-280">Para obter uma visão geral dos analisadores de código, consulte [visão geral dos analisadores de código-fonte](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="efe61-280">For an overview of code analyzers, see [Overview of source code analyzers](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="efe61-281">Habilite as seguintes regras Microsoft. CodeAnalysis. FxCopAnalyzers:</span><span class="sxs-lookup"><span data-stu-id="efe61-281">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="efe61-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): não use DataTable. ReadXml () com dados não confiáveis</span><span class="sxs-lookup"><span data-stu-id="efe61-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="efe61-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): não use DataSet. ReadXml () com dados não confiáveis</span><span class="sxs-lookup"><span data-stu-id="efe61-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="efe61-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): DataSet ou DataTable não seguro em tipo serializável pode ser vulnerável a ataques de execução remota de código</span><span class="sxs-lookup"><span data-stu-id="efe61-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="efe61-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): DataSet ou DataTable não seguro em tipo serializável</span><span class="sxs-lookup"><span data-stu-id="efe61-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="efe61-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): um DataSet não seguro ou DataTable no grafo de objeto desserializado pode ser vulnerável a ataques de execução remota de código</span><span class="sxs-lookup"><span data-stu-id="efe61-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="efe61-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): tipo de DataSet ou DataTable não seguro encontrado no grafo de objeto deserializável</span><span class="sxs-lookup"><span data-stu-id="efe61-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="efe61-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): tipo de DataSet ou DataTable não seguro no grafo de objeto deserializável da Web</span><span class="sxs-lookup"><span data-stu-id="efe61-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="efe61-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): garanta que a classe gerada automaticamente contendo DataSet. ReadXml () não seja usada com dados não confiáveis</span><span class="sxs-lookup"><span data-stu-id="efe61-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="efe61-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): DataSet ou DataTable não seguro em tipo serializável gerado automaticamente pode ser vulnerável a ataques de execução remota de código</span><span class="sxs-lookup"><span data-stu-id="efe61-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="efe61-291">Para obter mais informações sobre como configurar regras, consulte [usar analisadores de código](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span><span class="sxs-lookup"><span data-stu-id="efe61-291">For more information about configuring rules, see [Use code analyzers](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="efe61-292">As novas regras de segurança estão disponíveis nos seguintes pacotes NuGet:</span><span class="sxs-lookup"><span data-stu-id="efe61-292">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="efe61-293">Microsoft. CodeAnalysis. FxCopAnalyzers 3.3.0: para Visual Studio 2019 versão 16,3 ou posterior</span><span class="sxs-lookup"><span data-stu-id="efe61-293">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="efe61-294">Microsoft. CodeAnalysis. FxCopAnalyzers 2.9.11: para Visual Studio 2017 versão 15,9 ou posterior</span><span class="sxs-lookup"><span data-stu-id="efe61-294">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
