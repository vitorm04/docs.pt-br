---
description: -appconfig (opções do compilador C#)
title: -appconfig (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 8ee481851dc02bed5eb0a7c26fa8893e52d54a9f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157961"
---
# <a name="-appconfig-c-compiler-options"></a><span data-ttu-id="d3f14-103">-appconfig (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="d3f14-103">-appconfig (C# Compiler Options)</span></span>

<span data-ttu-id="d3f14-104">A opção do compilador **-appconfig** permite que um aplicativo em C# especifique o local de um arquivo de configuração de aplicativo (app.config) de um assembly para o CLR (Common Language Runtime) em tempo de associação do assembly.</span><span class="sxs-lookup"><span data-stu-id="d3f14-104">The **-appconfig** compiler option enables a C# application to specify the location of an assembly's application configuration (app.config) file to the common language runtime (CLR) at assembly binding time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f14-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3f14-105">Syntax</span></span>  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3f14-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d3f14-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="d3f14-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d3f14-107">Required.</span></span> <span data-ttu-id="d3f14-108">O arquivo de configuração de aplicativo que contém as configurações de associação de assembly.</span><span class="sxs-lookup"><span data-stu-id="d3f14-108">The application configuration file that contains assembly binding settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3f14-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3f14-109">Remarks</span></span>  

 <span data-ttu-id="d3f14-110">O **-appconfig** pode ser usado em cenários avançados, nos quais é necessário que um assembly referencie, ao mesmo temo, tanto a versão do .NET Framework quanto a versão do .NET Framework para a versão do Silverlight de um assembly de referência específico.</span><span class="sxs-lookup"><span data-stu-id="d3f14-110">One use of **-appconfig** is advanced scenarios in which an assembly has to reference both the .NET Framework version and the .NET Framework for Silverlight version of a particular reference assembly at the same time.</span></span> <span data-ttu-id="d3f14-111">Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) pode ter que referenciar a Área de Trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF incluído no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d3f14-111">For example, a XAML designer written in Windows Presentation Foundation (WPF) might have to reference both the WPF Desktop, for the designer's user interface, and the subset of WPF that is included with Silverlight.</span></span> <span data-ttu-id="d3f14-112">O mesmo assembly do designer deve acessar ambos os assemblies.</span><span class="sxs-lookup"><span data-stu-id="d3f14-112">The same designer assembly has to access both assemblies.</span></span> <span data-ttu-id="d3f14-113">Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.</span><span class="sxs-lookup"><span data-stu-id="d3f14-113">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span>  
  
 <span data-ttu-id="d3f14-114">A opção do compilador **-appconfig** permite a especificação do local de um arquivo app.config que desabilita o comportamento padrão por meio de uma marcação `<supportPortability>`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3f14-114">The **-appconfig** compiler option enables you to specify the location of an app.config file that disables the default behavior by using a `<supportPortability>` tag, as shown in the following example.</span></span>  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 <span data-ttu-id="d3f14-115">O compilador passa o local do arquivo para a lógica de associação de assembly do CLR.</span><span class="sxs-lookup"><span data-stu-id="d3f14-115">The compiler passes the location of the file to the CLR's assembly-binding logic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3f14-116">Caso o MSBuild (Microsoft Build Engine) seja usado para compilar o aplicativo, é possível definir a opção do compilador **-appconfig** adicionando uma marcação de propriedade ao arquivo .csproj.</span><span class="sxs-lookup"><span data-stu-id="d3f14-116">If you are using the Microsoft Build Engine (MSBuild) to build your application, you can set the **-appconfig** compiler option by adding a property tag to the .csproj file.</span></span> <span data-ttu-id="d3f14-117">Para usar o arquivo app.config que já está definido no projeto, adicione a marca de propriedade `<UseAppConfigForCompiler>` ao arquivo .csproj e defina seu valor para `true`.</span><span class="sxs-lookup"><span data-stu-id="d3f14-117">To use the app.config file that is already set in the project, add property tag `<UseAppConfigForCompiler>` to the .csproj file and set its value to `true`.</span></span> <span data-ttu-id="d3f14-118">Para especificar um arquivo app.config diferente, adicione a marca de propriedade `<AppConfigForCompiler>` e defina seu valor para o local do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3f14-118">To specify a different app.config file, add property tag `<AppConfigForCompiler>` and set its value to the location of the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f14-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3f14-119">Example</span></span>  

 <span data-ttu-id="d3f14-120">O exemplo a seguir mostra um arquivo app.config que habilita um aplicativo a referenciar as implementações do .NET Framework e do .NET Framework para Silverlight de qualquer assembly do .NET Framework que exista em ambas as implementações.</span><span class="sxs-lookup"><span data-stu-id="d3f14-120">The following example shows an app.config file that enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="d3f14-121">A opção do compilador **-appconfig** especifica o local desse arquivo app.config.</span><span class="sxs-lookup"><span data-stu-id="d3f14-121">The **-appconfig** compiler option specifies the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3f14-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="d3f14-122">See also</span></span>

- [<span data-ttu-id="d3f14-123">\<supportPortability> Elementos</span><span class="sxs-lookup"><span data-stu-id="d3f14-123">\<supportPortability> Element</span></span>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)
- [<span data-ttu-id="d3f14-124">Opções do compilador de C# listadas em ordem alfabética</span><span class="sxs-lookup"><span data-stu-id="d3f14-124">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
