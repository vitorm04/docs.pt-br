---
title: Wfc.exe (ferramenta de compilador de linha de comando do fluxo de trabalho)
description: Entenda wfc.exe, a ferramenta de compilador de linha de comando do fluxo de trabalho.
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844596"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="80bed-103">wfc.exe (ferramenta de compilador de linha de comando do fluxo de trabalho)</span><span class="sxs-lookup"><span data-stu-id="80bed-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>
> [!NOTE]
> <span data-ttu-id="80bed-104">Este material discute tipos e namespaces obsoletos.</span><span class="sxs-lookup"><span data-stu-id="80bed-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="80bed-105">A ferramenta de compilador de linha de comando de wfc.exe fluxo de trabalho funciona com arquivos de marcação de fluxo de trabalho antigos que têm a extensão de arquivo *. xoml* (obsoleto).</span><span class="sxs-lookup"><span data-stu-id="80bed-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="80bed-106">Processo de compilação</span><span class="sxs-lookup"><span data-stu-id="80bed-106">Compilation process</span></span>

<span data-ttu-id="80bed-107">Quando os fluxos de trabalho são compilados, os procedimentos a seguir são executados como parte do processo de compilação:</span><span class="sxs-lookup"><span data-stu-id="80bed-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="80bed-108">A validação é executada para garantir que as atividades de fluxo de trabalho sejam validadas com base nas regras que as atividades definiram para si mesmas.</span><span class="sxs-lookup"><span data-stu-id="80bed-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="80bed-109">Se houver erros de validação, o compilador retornará uma lista dos erros.</span><span class="sxs-lookup"><span data-stu-id="80bed-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="80bed-110">Uma classe parcial é gerada a partir da definição de marcação que é inserida no compilador.</span><span class="sxs-lookup"><span data-stu-id="80bed-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="80bed-111">O código é gerado para ajudar com a execução das atividades em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="80bed-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="80bed-112">As assinaturas de evento são geradas, o que ajuda as atividades a saber quando as atividades que eles contêm têm concluído a execução.</span><span class="sxs-lookup"><span data-stu-id="80bed-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="80bed-113">As classes parciais geradas a partir do arquivo de marcação e as classes parciais do arquivo de código são inseridas no compilador .NET Framework C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="80bed-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="80bed-114">A saída desse processo é o assembly .NET, WorkflowSample.dll.</span><span class="sxs-lookup"><span data-stu-id="80bed-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="80bed-115">Isso pode ser implantado para executar o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="80bed-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="80bed-116">Opções do compilador</span><span class="sxs-lookup"><span data-stu-id="80bed-116">Compiler options</span></span>

<span data-ttu-id="80bed-117">Esta seção mostra as opções para o compilador de linha de comando wfc.exe fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="80bed-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a><span data-ttu-id="80bed-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="80bed-118">Remarks</span></span>
> [!NOTE]
> <span data-ttu-id="80bed-119">Este material discute tipos e namespaces obsoletos.</span><span class="sxs-lookup"><span data-stu-id="80bed-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="80bed-120">Uma lista de tipos autorizados geralmente é definida no arquivo *wfc.exe.config* .</span><span class="sxs-lookup"><span data-stu-id="80bed-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="80bed-121">Durante a fase de validação da compilação do fluxo de trabalho, um documento de origem do fluxo de trabalho é rejeitado se ele ou o arquivo de regras complementares referencia diretamente qualquer tipo de .NET Framework não presente em uma lista de tipos autorizados.</span><span class="sxs-lookup"><span data-stu-id="80bed-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="80bed-122">A lista de tipos autorizados é um documento XML em que cada entrada indica um `Assembly` indicador, um, `Namespace` um `TypeName` e um { `True`&#124;`False` } autorizado.</span><span class="sxs-lookup"><span data-stu-id="80bed-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="80bed-123">`AuthorizedType` corresponde a uma entrada na lista.</span><span class="sxs-lookup"><span data-stu-id="80bed-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="80bed-124">As designações de caractere curinga, que podem ser usadas para incluir ou excluir namespaces completos, são permitidas.</span><span class="sxs-lookup"><span data-stu-id="80bed-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="80bed-125">Por exemplo, `Type="System.*"` inclui todos os tipos no <xref:System> , incluindo tipos contidos em namespaces filho.</span><span class="sxs-lookup"><span data-stu-id="80bed-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="80bed-126">O uso de uma lista de tipos autorizados é controlado pela <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> opção `'/checktypes'` .</span><span class="sxs-lookup"><span data-stu-id="80bed-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> <span data-ttu-id="80bed-127">Quando o `Type="System.*"` tipo está presente, é possível incluir outros tipos não pretendidos, como `Type="System.Configuration"` , para compilação.</span><span class="sxs-lookup"><span data-stu-id="80bed-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="80bed-128">Você deve ter cuidado e examinar cada um deles.</span><span class="sxs-lookup"><span data-stu-id="80bed-128">You should be cautious and review each one.</span></span> <span data-ttu-id="80bed-129">Para qualquer tipo que deva ser restringido, certifique-se de definir `Authorized` como `False` .</span><span class="sxs-lookup"><span data-stu-id="80bed-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="80bed-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80bed-130">See also</span></span>

- [<span data-ttu-id="80bed-131">Classe AuthorizedType</span><span class="sxs-lookup"><span data-stu-id="80bed-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
