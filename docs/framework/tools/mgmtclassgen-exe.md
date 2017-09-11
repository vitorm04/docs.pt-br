---
title: Mgmtclassgen.exe (Gerador de Classe Fortemente Tipada de Gerenciamento)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f83136265c4002f3ea4872b370b856bfacf4db3d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="d841e-102">Mgmtclassgen.exe (Gerador de Classe Fortemente Tipada de Gerenciamento)</span><span class="sxs-lookup"><span data-stu-id="d841e-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="d841e-103">A ferramenta Gerador de Classes Fortemente Tipadas de Gerenciamento permite gerar rapidamente uma classe gerenciada Early Bound para uma classe WMI (Instrumentação de Gerenciamento do Windows) especificada.</span><span class="sxs-lookup"><span data-stu-id="d841e-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="d841e-104">A classe gerada simplifica o código que você deve gravar para acessar uma instância da classe WMI.</span><span class="sxs-lookup"><span data-stu-id="d841e-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d841e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d841e-105">Syntax</span></span>  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="d841e-106">Argumento</span><span class="sxs-lookup"><span data-stu-id="d841e-106">Argument</span></span>|<span data-ttu-id="d841e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d841e-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d841e-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="d841e-108">*WMIClass*</span></span>|<span data-ttu-id="d841e-109">A classe WMI para a qual uma classe gerenciada Early Bound deve ser gerada.</span><span class="sxs-lookup"><span data-stu-id="d841e-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="d841e-110">Opção</span><span class="sxs-lookup"><span data-stu-id="d841e-110">Option</span></span>|<span data-ttu-id="d841e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d841e-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d841e-112">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="d841e-112">**/l**  *language*</span></span>|<span data-ttu-id="d841e-113">Especifica a linguagem na qual gerar a classe gerenciada Early Bound.</span><span class="sxs-lookup"><span data-stu-id="d841e-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="d841e-114">É possível especificar **CS** (C#, padrão), **VB** (Visual Basic), **MC** (C++) ou **JS** (JScript) como o argumento da linguagem.</span><span class="sxs-lookup"><span data-stu-id="d841e-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="d841e-115">**/m**  *machine*</span><span class="sxs-lookup"><span data-stu-id="d841e-115">**/m**  *machine*</span></span>|<span data-ttu-id="d841e-116">Especifica o computador ao qual se conectar, em que a classe WMI reside.</span><span class="sxs-lookup"><span data-stu-id="d841e-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="d841e-117">O padrão é o computador local.</span><span class="sxs-lookup"><span data-stu-id="d841e-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="d841e-118">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="d841e-118">**/n**  *path*</span></span>|<span data-ttu-id="d841e-119">Especifica o caminho para o namespace WMI que contém a classe WMI.</span><span class="sxs-lookup"><span data-stu-id="d841e-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="d841e-120">Se você não especificar essa opção, a ferramenta gerará o código para *WMIClass* no namespace **Root\cimv2** padrão.</span><span class="sxs-lookup"><span data-stu-id="d841e-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="d841e-121">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="d841e-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="d841e-122">Especifica o namespace do .NET no qual gerar a classe de código gerenciada.</span><span class="sxs-lookup"><span data-stu-id="d841e-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="d841e-123">Se você não especificar essa opção, a ferramenta gerará o namespace usando o namespace WMI e o prefixo do esquema.</span><span class="sxs-lookup"><span data-stu-id="d841e-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="d841e-124">O prefixo do esquema é a parte do nome da classe que antecede o caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="d841e-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="d841e-125">Por exemplo, para a classe **Win32_OperatingSystem** no namespace **Root\cimv2**, a ferramenta geraria a classe em **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="d841e-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="d841e-126">**/p**  *filepath*</span><span class="sxs-lookup"><span data-stu-id="d841e-126">**/p**  *filepath*</span></span>|<span data-ttu-id="d841e-127">Especifica o caminho para o arquivo no qual o código gerado deve ser salvo.</span><span class="sxs-lookup"><span data-stu-id="d841e-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="d841e-128">Se você não especificar essa opção, a ferramenta criará o arquivo no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d841e-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="d841e-129">Ela nomeia a classe e o arquivo em que gera a classe que usa o argumento *WMIClass*.</span><span class="sxs-lookup"><span data-stu-id="d841e-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="d841e-130">O nome da classe e do arquivo são iguais ao de *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="d841e-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="d841e-131">Se *WMIClass* contiver um caractere de sublinhado, a ferramenta usará a parte do nome de classe depois do caractere de sublinhado.</span><span class="sxs-lookup"><span data-stu-id="d841e-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="d841e-132">Por exemplo, se o nome *WMIClass* estiver no formato **Win32_LogicalDisk**, a classe e o arquivo gerados serão chamados de "logicaldisk".</span><span class="sxs-lookup"><span data-stu-id="d841e-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="d841e-133">Se já existir um arquivo, a ferramenta substituirá o arquivo existente.</span><span class="sxs-lookup"><span data-stu-id="d841e-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="d841e-134">**/pw**  *password*</span><span class="sxs-lookup"><span data-stu-id="d841e-134">**/pw**  *password*</span></span>|<span data-ttu-id="d841e-135">Especifica a senha a ser usada durante o logon em um computador especificado pela opção **/m**.</span><span class="sxs-lookup"><span data-stu-id="d841e-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="d841e-136">**/u**  *user name*</span><span class="sxs-lookup"><span data-stu-id="d841e-136">**/u**  *user name*</span></span>|<span data-ttu-id="d841e-137">Especifica o nome de usuário a ser usado durante o logon em um computador especificado pela opção **/m**.</span><span class="sxs-lookup"><span data-stu-id="d841e-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="d841e-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="d841e-138">**/?**</span></span>|<span data-ttu-id="d841e-139">Exibe sintaxe de comando e opções para a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d841e-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d841e-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="d841e-140">Remarks</span></span>  
 <span data-ttu-id="d841e-141">Mgmtclassgen.exe usa o método <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d841e-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="d841e-142">Por isso, é possível usar qualquer provedor de código personalizado para gerar código em linguagens gerenciadas que não sejam C#, Visual Basic e JScript.</span><span class="sxs-lookup"><span data-stu-id="d841e-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="d841e-143">As classes geradas são associadas ao esquema para o qual são geradas.</span><span class="sxs-lookup"><span data-stu-id="d841e-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="d841e-144">Se o esquema subjacente mudar, você deverá gerar novamente a classe se quiser refletir alterações no esquema.</span><span class="sxs-lookup"><span data-stu-id="d841e-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="d841e-145">A seguinte tabela mostra como tipos CIM (Common Information Model) são mapeados para tipos de dados em uma classe gerada:</span><span class="sxs-lookup"><span data-stu-id="d841e-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="d841e-146">Tipo CIM</span><span class="sxs-lookup"><span data-stu-id="d841e-146">CIM type</span></span>|<span data-ttu-id="d841e-147">Tipo de dados na classe gerada</span><span class="sxs-lookup"><span data-stu-id="d841e-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="d841e-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="d841e-148">CIM_SINT8</span></span>|<span data-ttu-id="d841e-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="d841e-149">**SByte**</span></span>|  
|<span data-ttu-id="d841e-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="d841e-150">CIM_UINT8</span></span>|<span data-ttu-id="d841e-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="d841e-151">**Byte**</span></span>|  
|<span data-ttu-id="d841e-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="d841e-152">CIM_SINT16</span></span>|<span data-ttu-id="d841e-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="d841e-153">**Int16**</span></span>|  
|<span data-ttu-id="d841e-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="d841e-154">CIM_UINT16</span></span>|<span data-ttu-id="d841e-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="d841e-155">**UInt16**</span></span>|  
|<span data-ttu-id="d841e-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="d841e-156">CIM_SINT32</span></span>|<span data-ttu-id="d841e-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="d841e-157">**Int32**</span></span>|  
|<span data-ttu-id="d841e-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="d841e-158">SIM_UINT32</span></span>|<span data-ttu-id="d841e-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="d841e-159">**UInt32**</span></span>|  
|<span data-ttu-id="d841e-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="d841e-160">CIM_SINT64</span></span>|<span data-ttu-id="d841e-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="d841e-161">**Int64**</span></span>|  
|<span data-ttu-id="d841e-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="d841e-162">CIM_UINT64</span></span>|<span data-ttu-id="d841e-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="d841e-163">**UInt64**</span></span>|  
|<span data-ttu-id="d841e-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="d841e-164">CIM_REAL32</span></span>|<span data-ttu-id="d841e-165">**Simples**</span><span class="sxs-lookup"><span data-stu-id="d841e-165">**Single**</span></span>|  
|<span data-ttu-id="d841e-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="d841e-166">CIM_REAL64</span></span>|<span data-ttu-id="d841e-167">**Duplo**</span><span class="sxs-lookup"><span data-stu-id="d841e-167">**Double**</span></span>|  
|<span data-ttu-id="d841e-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="d841e-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="d841e-169">**Booliano**</span><span class="sxs-lookup"><span data-stu-id="d841e-169">**Boolean**</span></span>|  
|<span data-ttu-id="d841e-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="d841e-170">CIM_String</span></span>|<span data-ttu-id="d841e-171">**Cadeia de caracteres**</span><span class="sxs-lookup"><span data-stu-id="d841e-171">**String**</span></span>|  
|<span data-ttu-id="d841e-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="d841e-172">CIM_DATETIME</span></span>|<span data-ttu-id="d841e-173">**DateTime** ou **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="d841e-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="d841e-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="d841e-174">CIM_REFERENCE</span></span>|<span data-ttu-id="d841e-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="d841e-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="d841e-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="d841e-176">CIM_CHAR16</span></span>|<span data-ttu-id="d841e-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="d841e-177">**Char**</span></span>|  
|<span data-ttu-id="d841e-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="d841e-178">CIM_OBJECT</span></span>|<span data-ttu-id="d841e-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="d841e-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="d841e-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="d841e-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="d841e-181">**Object**</span><span class="sxs-lookup"><span data-stu-id="d841e-181">**Object**</span></span>|  
|<span data-ttu-id="d841e-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="d841e-182">CIM_ARRAY</span></span>|<span data-ttu-id="d841e-183">Matriz dos objetos mencionados acima</span><span class="sxs-lookup"><span data-stu-id="d841e-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="d841e-184">Observer os seguintes comportamentos quando você gera uma classe WMI:</span><span class="sxs-lookup"><span data-stu-id="d841e-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
-   <span data-ttu-id="d841e-185">É possível que uma propriedade ou um método público padrão tenha o mesmo nome de uma propriedade ou um método existente.</span><span class="sxs-lookup"><span data-stu-id="d841e-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="d841e-186">Se isso ocorrer, a ferramenta alterará o nome da propriedade ou do método na classe gerada para evitar conflitos de nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="d841e-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="d841e-187">É possível que o nome de uma propriedade ou de um método em uma classe gerada seja uma palavra-chave na linguagem de programação de destino.</span><span class="sxs-lookup"><span data-stu-id="d841e-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="d841e-188">Se isso ocorrer, a ferramenta alterará o nome da propriedade ou do método na classe gerada para evitar conflitos de nomenclatura.</span><span class="sxs-lookup"><span data-stu-id="d841e-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="d841e-189">No WMI, os qualificadores são os modificadores que contêm informações para descrever uma classe, uma instância, uma propriedade ou um método.</span><span class="sxs-lookup"><span data-stu-id="d841e-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="d841e-190">O WMI usa qualificadores padrão como **Leitura**, **Gravação** e **Chave** para descrever uma propriedade em uma classe gerada.</span><span class="sxs-lookup"><span data-stu-id="d841e-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="d841e-191">Por exemplo, uma propriedade modificada com um qualificador **Leitura** é definida apenas com um acessador **get** da propriedade na classe gerada.</span><span class="sxs-lookup"><span data-stu-id="d841e-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="d841e-192">Como uma propriedade marcada com o qualificador **Leitura** deve ser somente leitura, um acessador **set** não é definido.</span><span class="sxs-lookup"><span data-stu-id="d841e-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
-   <span data-ttu-id="d841e-193">Uma propriedade numérica pode ser modificada pelos qualificadores **Values** e **ValueMaps** para indicar que a propriedade pode ser definida somente como valores permitidos especificados.</span><span class="sxs-lookup"><span data-stu-id="d841e-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="d841e-194">Uma enumeração é gerada com **Values** e **ValueMaps** e a propriedade é mapeada para a enumeração.</span><span class="sxs-lookup"><span data-stu-id="d841e-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
-   <span data-ttu-id="d841e-195">O WMI usa o termo singleton para descrever uma classe que só pode ter uma instância.</span><span class="sxs-lookup"><span data-stu-id="d841e-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="d841e-196">Por isso, o construtor padrão de uma classe singleton inicializará a classe com a única instância da classe.</span><span class="sxs-lookup"><span data-stu-id="d841e-196">Therefore, the default constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
-   <span data-ttu-id="d841e-197">Uma classe WMI pode ter as propriedades que são objetos.</span><span class="sxs-lookup"><span data-stu-id="d841e-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="d841e-198">Ao gerar uma classe fortemente tipada para esse tipo de classe WMI, você deve levar em consideração a geração de classes fortemente tipadas para os tipos das propriedades de objeto inseridas.</span><span class="sxs-lookup"><span data-stu-id="d841e-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="d841e-199">Isso permitirá acessar os objetos inseridos de maneira fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="d841e-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="d841e-200">Observe que o código gerado talvez não seja capaz de detectar o tipo de objeto inserido.</span><span class="sxs-lookup"><span data-stu-id="d841e-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="d841e-201">Nesse caso, um comentário será criado no código gerado para notificar você desse problema.</span><span class="sxs-lookup"><span data-stu-id="d841e-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="d841e-202">Em seguida, é possível modificar o código gerado para tipar a propriedade para a outra classe gerada.</span><span class="sxs-lookup"><span data-stu-id="d841e-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
-   <span data-ttu-id="d841e-203">No WMI, o valor de dados do tipo de dados CIM_DATETIME pode representar uma data e hora específicas ou um intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="d841e-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="d841e-204">Se o valor de dados representar uma data e hora, o tipo de dados na classe gerada será **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="d841e-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="d841e-205">Se o valor de dados representar um intervalo de tempo, o tipo de dados na classe gerada será **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="d841e-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="d841e-206">Também é possível gerar uma classe fortemente tipada usando-se a Extensão de Gerenciamento do Gerenciador de Servidores no Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="d841e-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="d841e-207">Para obter mais informações sobre WMI, consulte o tópico **Instrumentação de Gerenciamento do Windows** na documentação do SDK da Plataforma.</span><span class="sxs-lookup"><span data-stu-id="d841e-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d841e-208">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d841e-208">Examples</span></span>  
 <span data-ttu-id="d841e-209">O comando a seguir gera uma classe gerenciada no código do C# para a classe WMI **Win32_LogicalDisk** no namespace **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="d841e-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="d841e-210">A ferramenta grava a classe gerenciada no arquivo de origem em c:\disk.cs no namespace **ROOT.CIMV2.Win32**.</span><span class="sxs-lookup"><span data-stu-id="d841e-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="d841e-211">O código a seguir mostra como usar uma classe gerada programaticamente.</span><span class="sxs-lookup"><span data-stu-id="d841e-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="d841e-212">Primeiro, uma instância da classe é enumerada e o caminho é impresso.</span><span class="sxs-lookup"><span data-stu-id="d841e-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="d841e-213">Em seguida, uma instância da classe gerada a ser inicializada é criada com uma instância de WMI.</span><span class="sxs-lookup"><span data-stu-id="d841e-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="d841e-214">`Process` é a classe gerada para **Win32_Process** e `LogicalDisk` é a classe gerada para **Win32_LogicalDisk** no namespace **Root\cimv2**.</span><span class="sxs-lookup"><span data-stu-id="d841e-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d841e-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d841e-215">See Also</span></span>  
 <span data-ttu-id="d841e-216"><xref:System.Management></span><span class="sxs-lookup"><span data-stu-id="d841e-216"><xref:System.Management></span></span>   
 <span data-ttu-id="d841e-217"><xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d841e-217"><xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="d841e-218"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d841e-218"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName></span></span>   
 <span data-ttu-id="d841e-219">[Ferramentas](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="d841e-219">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 [<span data-ttu-id="d841e-220">Prompts de Comando</span><span class="sxs-lookup"><span data-stu-id="d841e-220">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

