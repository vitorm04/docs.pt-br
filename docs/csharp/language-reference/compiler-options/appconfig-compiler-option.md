---
title: "-appconfig (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords: /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca752c6264d0ee886aa4c248738097e0caf1d756
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="appconfig-c-compiler-options"></a><span data-ttu-id="8b848-102">/appconfig (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="8b848-102">/appconfig (C# Compiler Options)</span></span>
<span data-ttu-id="8b848-103">A opção do compilador **/appconfig** habilita um aplicativo em C# a especificar o local de um arquivo de configuração de aplicativo (app.config) de um assembly para o Common Language Runtime (CLR) no tempo de associação do assembly.</span><span class="sxs-lookup"><span data-stu-id="8b848-103">The **/appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b848-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b848-104">Syntax</span></span>  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8b848-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8b848-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="8b848-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8b848-106">Required.</span></span> <span data-ttu-id="8b848-107">O arquivo de configuração de aplicativo que contém as configurações de associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="8b848-107">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b848-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b848-108">Remarks</span></span>  
 <span data-ttu-id="8b848-109">O **/appconfig** pode ser usado em cenários avançados, nos quais é necessário que um assembly referencie simultaneamente a versão do .NET Framework e a versão do .NET Framework para o Silverlight de um assembly de referência específico.</span><span class="sxs-lookup"><span data-stu-id="8b848-109">One use of **/appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="8b848-110">Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) pode ter que referenciar a Área de Trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF incluído no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="8b848-110">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="8b848-111">O mesmo assembly do designer deve acessar ambos os assemblies.</span><span class="sxs-lookup"><span data-stu-id="8b848-111">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="8b848-112">Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.</span><span class="sxs-lookup"><span data-stu-id="8b848-112">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="8b848-113">A opção do compilador **/appconfig** habilita a especificação do local de um arquivo app.config que desabilita o comportamento padrão por meio de uma marca `<supportPortability>`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8b848-113">The **/appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="8b848-114">O compilador passa o local do arquivo para a lógica de associação de assembly do CLR.</span><span class="sxs-lookup"><span data-stu-id="8b848-114">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b848-115">Caso o Microsoft Build Engine (MSBuild) seja usado para compilar o aplicativo, é possível definir a opção do compilador **/appconfig** adicionando uma marca de propriedade ao arquivo .csproj.</span><span class="sxs-lookup"><span data-stu-id="8b848-115">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **/appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="8b848-116">Para usar o arquivo app.config que já está definido no projeto, adicione a marca de propriedade `<UseAppConfigForCompiler>` ao arquivo .csproj e defina seu valor para `true`.</span><span class="sxs-lookup"><span data-stu-id="8b848-116">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="8b848-117">Para especificar um arquivo app.config diferente, adicione a marca de propriedade `<AppConfigForCompiler>` e defina seu valor para o local do arquivo.</span><span class="sxs-lookup"><span data-stu-id="8b848-117">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b848-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b848-118">Example</span></span>  
 <span data-ttu-id="8b848-119">O exemplo a seguir mostra um arquivo app.config que habilita um aplicativo a referenciar as implementações do .NET Framework e do .NET Framework para Silverlight de qualquer assembly do .NET Framework que exista em ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="8b848-119">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="8b848-120">A opção do compilador **/appconfig** especifica o local desse arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="8b848-120">The **/appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b848-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b848-121">See Also</span></span>  
 [<span data-ttu-id="8b848-122">\<supportPortability > elemento</span><span class="sxs-lookup"><span data-stu-id="8b848-122">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [<span data-ttu-id="8b848-123">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="8b848-123">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
