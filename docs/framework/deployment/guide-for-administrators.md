---
title: "Guia de implantação do .NET Framework para administradores"
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
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
caps.latest.revision: 40
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 07b7381ddc94e3bc40a4eb0ed546f9526b57600a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="net-framework-deployment-guide-for-administrators"></a><span data-ttu-id="a0d4e-102">Guia de implantação do .NET Framework para administradores</span><span class="sxs-lookup"><span data-stu-id="a0d4e-102">.NET Framework Deployment Guide for Administrators</span></span>
<span data-ttu-id="a0d4e-103">Este artigo passo a passo descreve como um administrador de sistemas pode implantar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e suas dependências de sistema pela rede usando o Microsoft System Center Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-103">This step-by-step article describes how a system administrator can deploy the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] and its system dependencies across a network by using Microsoft System Center Configuration Manager.</span></span> <span data-ttu-id="a0d4e-104">Este artigo pressupõe que todos os computadores clientes de destino atendem aos requisitos mínimos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-104">This article assumes that all target client computers meet the minimum requirements for the .NET Framework.</span></span> <span data-ttu-id="a0d4e-105">Para obter uma lista dos requisitos de hardware e software para instalar o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consulte [Requisitos do sistema](../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-105">For a list of the software and hardware requirements for installing the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], see [System Requirements](../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0d4e-106">O software referenciado neste documento, incluindo, sem restrição, o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager e o Active Directory, estão sujeitos aos termos de licença e condições.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-106">The software referenced in this document, including, without limitation, the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager, and Active Directory, are each subject to license terms and conditions.</span></span> <span data-ttu-id="a0d4e-107">Essas instruções assumem que esses termos de licença e condições foram examinados e aceitos pelos licenciados apropriados do software.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-107">These instructions assume that such license terms and conditions have been reviewed and accepted by the appropriate licensees of the software.</span></span> <span data-ttu-id="a0d4e-108">Essas instruções não renunciam nenhum dos termos e condições dos contratos de tal licença.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-108">These instructions do not waive any of the terms and conditions of such license agreements.</span></span>  
>   
>  <span data-ttu-id="a0d4e-109">Para saber mais sobre suporte ao .NET Framework, confira [Política de ciclo de vida de suporte do Microsoft .NET Framework](http://go.microsoft.com/fwlink/?LinkId=196607) no site de Suporte da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-109">For information about support for the .NET Framework, see [Microsoft .NET Framework Support Lifecycle Policy](http://go.microsoft.com/fwlink/?LinkId=196607) on the Microsoft Support website.</span></span>  
  
 <span data-ttu-id="a0d4e-110">Esse tópico contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-110">This topic contains the following sections:</span></span>  
  
 <span data-ttu-id="a0d4e-111">[O processo de implantação](#the_deployment_process) </span><span class="sxs-lookup"><span data-stu-id="a0d4e-111">[The deployment process](#the_deployment_process) </span></span>  
 <span data-ttu-id="a0d4e-112">[Implantando o .NET Framework](#deploying_in_a_test_environment) </span><span class="sxs-lookup"><span data-stu-id="a0d4e-112">[Deploying the .NET Framework](#deploying_in_a_test_environment) </span></span>  
 [<span data-ttu-id="a0d4e-113">Criar uma coleção</span><span class="sxs-lookup"><span data-stu-id="a0d4e-113">Create a collection</span></span>](#creating_a_collection)  
 [<span data-ttu-id="a0d4e-114">Criar um pacote e um programa</span><span class="sxs-lookup"><span data-stu-id="a0d4e-114">Create a package and program</span></span>](#creating_a_package)  
 [<span data-ttu-id="a0d4e-115">Selecionar um ponto de distribuição</span><span class="sxs-lookup"><span data-stu-id="a0d4e-115">Select a distribution point</span></span>](#select_dist_point)  
 [<span data-ttu-id="a0d4e-116">Implantar o pacote</span><span class="sxs-lookup"><span data-stu-id="a0d4e-116">Deploy the package</span></span>](#deploying_package)  
[<span data-ttu-id="a0d4e-117">Recursos</span><span class="sxs-lookup"><span data-stu-id="a0d4e-117">Resources</span></span>](#resources)  
[<span data-ttu-id="a0d4e-118">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a0d4e-118">Troubleshooting</span></span>](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a><span data-ttu-id="a0d4e-119">O processo de implantação</span><span class="sxs-lookup"><span data-stu-id="a0d4e-119">The deployment process</span></span>  
 <span data-ttu-id="a0d4e-120">Quando a infraestrutura de suporte estiver disponível, use o System Center 2012 Configuration Manager para implantar o pacote .NET Framework redistribuível em computadores na rede.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-120">When you have the supporting infrastructure in place, you use System Center 2012 Configuration Manager to deploy the .NET Framework redistributable package to computers on the network.</span></span> <span data-ttu-id="a0d4e-121">Estabelecer uma infraestrutura envolve criar e definir cinco áreas principais: coleções, um pacote e programa para o software, pontos de distribuição e implantações.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-121">Building the infrastructure involves creating and defining five primary areas: collections, a package and program for the software, distribution points, and deployments.</span></span>  
  
-   <span data-ttu-id="a0d4e-122">**Coleções** são grupos de recursos do Configuration Manager, como usuários, grupos de usuários ou computadores, nos quais o .NET Framework é implantado.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-122">**Collections** are groups of Configuration Manager resources, such as users, user groups, or computers, to which the .NET Framework is deployed.</span></span> <span data-ttu-id="a0d4e-123">Para obter mais informações, consulte [Coleções no Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-123">For more information, see [Collections in Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a0d4e-124">**Pacotes e programas** geralmente representam aplicativos de software a serem instalados em um computador cliente, mas também podem conter arquivos individuais, atualizações ou até mesmo comandos individuais.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-124">**Packages and programs** typically represent software applications to be installed on a client computer, but they might also contain individual files, updates, or even individual commands.</span></span> <span data-ttu-id="a0d4e-125">Para obter mais informações, consulte [Pacotes e programas no Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-125">For more information, see [Packages and Programs in Configuration Manager](http://technet.microsoft.com/library/gg699369.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a0d4e-126">**Pontos de distribuição** são funções do sistema de sites do Configuration Manager que armazenam os arquivos necessários para que o software seja executado em computadores cliente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-126">**Distribution points** are Configuration Manager site system roles that store files required for software to run on client computers.</span></span> <span data-ttu-id="a0d4e-127">Quando o cliente do Configuration Manager recebe e processa uma implantação de software, ele contata um ponto de distribuição para baixar o conteúdo associado ao software e iniciar o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-127">When the Configuration Manager client receives and processes a software deployment, it contacts a distribution point to download the content associated with the software and to start the installation process.</span></span> <span data-ttu-id="a0d4e-128">Para obter mais informações, consulte [Introdução ao gerenciamento de conteúdo no Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-128">For more information, see [Introduction to content Management in Configuration Manager](http://technet.microsoft.com/library/gg682083.aspx) in the Configuration Manager documentation library.</span></span>  
  
-   <span data-ttu-id="a0d4e-129">**Implantações** instruem os membros aplicáveis da coleção de destino especificada a instalarem o pacote de software.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-129">**Deployments** instruct applicable members of the specified target collection to install the software package.</span></span> <span data-ttu-id="a0d4e-130">Para obter mais informações, consulte [Como implantar aplicativos no Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-130">For more information, see [How to Deploy Applications in Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx) in the Configuration Manager documentation library.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0d4e-131">Os procedimentos neste tópico contém configurações comuns para criar e implantar um pacote e um programa e podem não abranger todas as configurações possíveis.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-131">The procedures in this topic contain typical settings for creating and deploying a package and program, and might not cover all possible settings.</span></span> <span data-ttu-id="a0d4e-132">Para obter outras opções de implantação do Configuration Manager, consulte a [Biblioteca de documentação do Configuration Manager](http://technet.microsoft.com/library/gg682041.aspx).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-132">For other Configuration Manager deployment options, see the [Configuration Manager Documentation Library](http://technet.microsoft.com/library/gg682041.aspx).</span></span>  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a><span data-ttu-id="a0d4e-133">Implantando o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a0d4e-133">Deploying the .NET Framework</span></span>  
 <span data-ttu-id="a0d4e-134">Você pode usar o System Center 2012 Configuration Manager para implantar uma instalação silenciosa do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], onde os usuários não interagem com o processo de instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-134">You can use System Center 2012 Configuration Manager to deploy a silent installation of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], where the users do not interact with the installation process.</span></span> <span data-ttu-id="a0d4e-135">Siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-135">Follow these steps:</span></span>  
  
1.  <span data-ttu-id="a0d4e-136">[Crie uma coleção](#creating_a_collection).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-136">[Create a collection](#creating_a_collection).</span></span>  
  
2.  <span data-ttu-id="a0d4e-137">[Crie um pacote e um programa para o .NET Framework redistribuível](#creating_a_package).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-137">[Create a package and program for the .NET Framework redistributable](#creating_a_package).</span></span>  
  
3.  <span data-ttu-id="a0d4e-138">[Selecione um ponto de distribuição](#select_dist_point).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-138">[Select a distribution point](#select_dist_point).</span></span>  
  
4.  <span data-ttu-id="a0d4e-139">[Implante o pacote](#deploying_package).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-139">[Deploy the package](#deploying_package).</span></span>  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a><span data-ttu-id="a0d4e-140">Crie uma coleção</span><span class="sxs-lookup"><span data-stu-id="a0d4e-140">Create a collection</span></span>  
 <span data-ttu-id="a0d4e-141">Nesta etapa, você selecionará os computadores nos quais pacote e o programa serão implantados e os agrupará em uma coleção de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-141">In this step, you select the computers to which you will deploy the package and program, and group them into a device collection.</span></span> <span data-ttu-id="a0d4e-142">Para criar uma coleção no Configuration Manager, você pode usar regras de associação diretas (onde você especifica manualmente os membros da coleção) ou regras de consulta (onde o Configuration Manager determina os membros da coleção com base em critérios especificados).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-142">To create a collection in Configuration Manager, you can use direct membership rules (where you manually specify the collection members) or query rules (where Configuration Manager determines the collection members based on criteria you specify).</span></span> <span data-ttu-id="a0d4e-143">Para obter mais informações sobre regras de associação, inclusive regras diretas e de consulta, consulte [Introdução às coleções no Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-143">For more information about membership rules, including queries and direct rules, see [Introduction to Collections in Configuration Manager](http://technet.microsoft.com/library/gg682177.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
 <span data-ttu-id="a0d4e-144">Para criar uma coleção:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-144">To create a collection:</span></span>  
  
1.  <span data-ttu-id="a0d4e-145">No console do Configuration Manager, escolha **Ativos e Conformidade**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-145">In the Configuration Manager console, choose **Assets and Compliance**.</span></span>  
  
2.  <span data-ttu-id="a0d4e-146">No espaço de trabalho **Ativos e Conformidade**, escolha **Coleções de Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-146">In the **Assets and Compliance** workspace, choose **Device Collections**.</span></span>  
  
3.  <span data-ttu-id="a0d4e-147">Na guia **Início** do grupo **Criar**, escolha **Criar Coleção de Dispositivos**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-147">On the **Home** tab in the **Create** group, choose **Create Device Collection**.</span></span>  
  
4.  <span data-ttu-id="a0d4e-148">Na página **Geral** do **Assistente de Criação de Coleção de Dispositivos**, insira um nome para a coleção.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-148">On the **General** page of the **Create Device Collection Wizard**, enter a name for the collection.</span></span>  
  
5.  <span data-ttu-id="a0d4e-149">Escolha **Procurar** para especificar uma coleção de restrição.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-149">Choose **Browse** to specify a limiting collection.</span></span>  
  
6.  <span data-ttu-id="a0d4e-150">Na página **Regras de Associação**, escolha **Adicionar Regra** e escolha **Regra Direta** para abrir o **Assistente de Criação de Regra de Associação Direta**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-150">On the **Membership Rules** page, choose **Add Rule**, and then choose **Direct Rule** to open the **Create Direct Membership Rule Wizard**.</span></span> <span data-ttu-id="a0d4e-151">Escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-151">Choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a0d4e-152">Na página **Pesquisar Recursos**, na lista **Classe de recurso**, escolha **Recurso do Sistema**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-152">On the **Search for Resources** page, in the **Resource class** list, choose **System Resource**.</span></span> <span data-ttu-id="a0d4e-153">Na lista **Nome do atributo**, escolha **Nome**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-153">In the **Attribute name** list, choose **Name**.</span></span> <span data-ttu-id="a0d4e-154">No campo **Valor**, insira `%` e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-154">In the **Value** field, enter `%`, and then choose **Next**.</span></span>  
  
8.  <span data-ttu-id="a0d4e-155">Na página **Selecionar Recursos**, marque a caixa de seleção para cada computador no qual você deseja implantar o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-155">On the **Select Resources** page, select the check box for each computer that you want to deploy the .NET Framework to.</span></span> <span data-ttu-id="a0d4e-156">Escolha **Avançar** e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-156">Choose **Next**, and then complete the wizard.</span></span>  
  
9. <span data-ttu-id="a0d4e-157">Na página **Regras de Associação** do **Assistente de Criação de Coleção de Dispositivos**, escolha **Avançar** e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-157">On the **Membership Rules** page of the **Create Device Collection Wizard**, choose **Next**, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="a0d4e-158">Para obter mais informações sobre coleções, consulte [Coleções no Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-158">For more information about collections, see [Collections in Configuration Manager](http://technet.microsoft.com/library/bb693730.aspx) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a><span data-ttu-id="a0d4e-159">Crie um pacote e programa para o pacote .NET Framework redistribuível</span><span class="sxs-lookup"><span data-stu-id="a0d4e-159">Create a package and program for the .NET Framework redistributable package</span></span>  
 <span data-ttu-id="a0d4e-160">As etapas a seguir criam, manualmente, um pacote para o .NET Framework redistribuível.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-160">The following steps create a package for the .NET Framework redistributable manually.</span></span> <span data-ttu-id="a0d4e-161">O pacote conterá os parâmetros especificados para instalar o .NET Framework e o local de onde o pacote será distribuído para os computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-161">The package contains the specified parameters for installing the .NET Framework and the location from where the package will be distributed to the target computers.</span></span>  
  
 <span data-ttu-id="a0d4e-162">Para criar um pacote:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-162">To create a package:</span></span>  
  
1.  <span data-ttu-id="a0d4e-163">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-163">In the Configuration Manager console, choose **Software Library**..</span></span>  
  
2.  <span data-ttu-id="a0d4e-164">No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-164">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a0d4e-165">Na guia **Início**, no grupo **Criar**, escolha **Criar Pacote**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-165">On the **Home** tab, in the **Create** group, choose **Create Package**.</span></span>  
  
4.  <span data-ttu-id="a0d4e-166">Na página **Pacote** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-166">On the **Package** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    -   <span data-ttu-id="a0d4e-167">Nome: `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="a0d4e-167">Name: `.NET Framework 4.5`</span></span>  
  
    -   <span data-ttu-id="a0d4e-168">Fabricante: `Microsoft`</span><span class="sxs-lookup"><span data-stu-id="a0d4e-168">Manufacturer: `Microsoft`</span></span>  
  
    -   <span data-ttu-id="a0d4e-169">Idioma.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-169">Language.</span></span> `English (US)`  
  
5.  <span data-ttu-id="a0d4e-170">Escolha **Este pacote contém arquivos de origem** e **Procurar** para selecionar a pasta de rede ou local que contém os arquivos de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-170">Choose **This package contains source files**, and then choose **Browse** to select the local or network folder that contains the .NET Framework installation files.</span></span> <span data-ttu-id="a0d4e-171">Após selecionar a pasta, escolha **OK** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-171">When you have selected the folder, choose **OK**, and then choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a0d4e-172">Na página **Tipo de Programa** do assistente, escolha **Programa Padrão** e **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-172">On the **Program Type** page of the wizard, choose **Standard Program**, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a0d4e-173">Na página **Programa** do **Assistente para Criar Pacote e Programa**, insira as seguintes informações:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-173">On the **Program** page of the **Create Package and Program Wizard**, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="a0d4e-174">**Nome:** `.NET Framework 4.5`</span><span class="sxs-lookup"><span data-stu-id="a0d4e-174">**Name:** `.NET Framework 4.5`</span></span>  
  
    2.  <span data-ttu-id="a0d4e-175">**Linha de comando:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (as opções de linha de comando são descritas na tabela após estas etapas)</span><span class="sxs-lookup"><span data-stu-id="a0d4e-175">**Command line:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (command-line options are described in the table after these steps)</span></span>  
  
    3.  <span data-ttu-id="a0d4e-176">**Executar:** escolha **Oculto**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-176">**Run:** Choose **Hidden**.</span></span>  
  
    4.  <span data-ttu-id="a0d4e-177">**O programa pode ser executado:** escolha a opção que especifica que o programa pode ser executado independentemente de um usuário estar conectado.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-177">**Program can run:** Choose the option that specifies that the program can run regardless of whether a user is logged on.</span></span>  
  
8.  <span data-ttu-id="a0d4e-178">Na página **Requisitos**, escolha **Avançar** para aceitar os valores padrão e conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-178">On the **Requirements** page, choose **Next** to accept the default values, and then complete the wizard.</span></span>  
  
 <span data-ttu-id="a0d4e-179">A tabela a seguir descreve as opções de linha de comando especificadas na etapa 7.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-179">The following table describes the command-line options specified in step 7.</span></span>  
  
|<span data-ttu-id="a0d4e-180">Opção</span><span class="sxs-lookup"><span data-stu-id="a0d4e-180">Option</span></span>|<span data-ttu-id="a0d4e-181">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d4e-181">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a0d4e-182">**/q**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-182">**/q**</span></span>|<span data-ttu-id="a0d4e-183">Define o modo silencioso.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-183">Sets quiet mode.</span></span> <span data-ttu-id="a0d4e-184">Nenhuma entrada do usuário é necessária e nenhuma saída é mostrada.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-184">No user input is required, and no output is shown.</span></span>|  
|<span data-ttu-id="a0d4e-185">**/norestart**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-185">**/norestart**</span></span>|<span data-ttu-id="a0d4e-186">Impede que o programa de instalação reinicialize automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-186">Prevents the Setup program from rebooting automatically.</span></span> <span data-ttu-id="a0d4e-187">Se você usar essa opção, o Configuration Manager deverá processar a reinicialização do computador.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-187">If you use this option, Configuration Manager must handle the computer restart.</span></span>|  
|<span data-ttu-id="a0d4e-188">**/chainingpackage** *PackageName*</span><span class="sxs-lookup"><span data-stu-id="a0d4e-188">**/chainingpackage** *PackageName*</span></span>|<span data-ttu-id="a0d4e-189">Especifica o nome do pacote que está fazendo o encadeamento.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-189">Specifies the name of the package that is doing the chaining.</span></span> <span data-ttu-id="a0d4e-190">Essa informação é relatada com outras informações da sessão de instalação para aqueles que se inscreveram no [Programa de Aperfeiçoamento da Experiência do Usuário da Microsoft (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-190">This information is reported with other installation session information for those who have signed up for the [Microsoft Customer Experience Improvement Program (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244).</span></span> <span data-ttu-id="a0d4e-191">Se o nome do pacote contiver espaços, use aspas duplas como delimitadores: **/chainingpackage "Chaining Product"**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-191">If the package name includes spaces, use double quotation marks as delimiters; for example: **/chainingpackage "Chaining Product"**.</span></span>|  
  
 <span data-ttu-id="a0d4e-192">Estas etapas criam um pacote chamado .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-192">These steps create a package named .NET Framework 4.5.</span></span> <span data-ttu-id="a0d4e-193">O programa implanta uma instalação silenciosa do .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-193">The program deploys a silent installation of the .NET Framework 4.5.</span></span> <span data-ttu-id="a0d4e-194">Em uma instalação silenciosa, os usuários não interagem com o processo de instalação e a aplicação encadeada precisa capturar o código de retorno e lidar com a reinicialização; consulte [Obtendo informações de progresso de um pacote de instalação](http://go.microsoft.com/fwlink/?LinkId=179606) na Biblioteca MSDN.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-194">In a silent installation, users do not interact with the installation process, and the chaining application has to capture the return code and handle rebooting; see [Getting Progress Information from an Installation Package](http://go.microsoft.com/fwlink/?LinkId=179606) in the MSDN Library.</span></span>  
  
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a><span data-ttu-id="a0d4e-195">Selecione um ponto de distribuição</span><span class="sxs-lookup"><span data-stu-id="a0d4e-195">Select a distribution point</span></span>  
 <span data-ttu-id="a0d4e-196">Para distribuir o pacote e o programa para computadores clientes de um servidor, primeiro designe um sistema de site como um ponto de distribuição e distribua o pacote para o ponto de distribuição.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-196">To distribute the package and program to client computers from a server, you must first designate a site system as a distribution point and then distribute the package to the distribution point.</span></span>  
  
 <span data-ttu-id="a0d4e-197">Use as etapas a seguir para selecionar um ponto de distribuição para o pacote .NET Framework 4.5 criado na seção anterior:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-197">Use the following steps to select a distribution point for the .NET Framework 4.5 package you created in the previous section:</span></span>  
  
1.  <span data-ttu-id="a0d4e-198">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-198">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="a0d4e-199">No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-199">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a0d4e-200">Na lista de pacotes, selecione o pacote **.NET Framework 4.5** que você criou na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-200">From the list of packages, select the package **.NET Framework 4.5** that you created in the previous section.</span></span>  
  
4.  <span data-ttu-id="a0d4e-201">Na guia **Início** do grupo **Implantação**, escolha **Distribuir Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-201">On the **Home** tab, in the **Deployment** group, choose **Distribute Content**.</span></span>  
  
5.  <span data-ttu-id="a0d4e-202">Na guia **Geral** do **Assistente para Distribuir Conteúdo**, escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-202">On the **General** tab of the **Distribute Content Wizard**, choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a0d4e-203">Na página **Destino de Conteúdo** do assistente, escolha **Adicionar** e **Ponto de Distribuição**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-203">On the **Content Destination** page of the wizard, choose **Add**, and then choose **Distribution Point**.</span></span>  
  
7.  <span data-ttu-id="a0d4e-204">Na caixa de diálogo **Adicionar Pontos de Distribuição**, selecione os pontos de distribuição que hospedarão o pacote e o programa e escolha **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-204">In the **Add Distribution Points** dialog box, select the distribution point(s) that will host the package and program, and then choose **OK**.</span></span>  
  
8.  <span data-ttu-id="a0d4e-205">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-205">Complete the wizard.</span></span>  
  
 <span data-ttu-id="a0d4e-206">O pacote agora contém todas as informações que você precisa para implantar silenciosamente o .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-206">The packagenow contains all the information you need to silently deploy the .NET Framework 4.5.</span></span> <span data-ttu-id="a0d4e-207">Antes de você implantar o pacote e o programa, verifique se ele foi instalado no ponto de distribuição, consulte a seção "Monitorar conteúdo" em [Operações e manutenção para o gerenciamento de conteúdo no Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) na biblioteca de documentação do Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-207">Before you deploy the package and program, verify that it was installed on the distribution point; see the "Monitor Content" section of [Operations and Maintenance for Content Management in Configuration Manager](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) in the Configuration Manager Documentation Library.</span></span>  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a><span data-ttu-id="a0d4e-208">Implante o pacote</span><span class="sxs-lookup"><span data-stu-id="a0d4e-208">Deploy the package</span></span>  
 <span data-ttu-id="a0d4e-209">Para implantar o pacote e o programa .NET Framework 4.5:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-209">To deploy the .NET Framework 4.5 package and program:</span></span>  
  
1.  <span data-ttu-id="a0d4e-210">No console do Configuration Manager, escolha **Biblioteca de Software**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-210">In the Configuration Manager console, choose **Software Library**.</span></span>  
  
2.  <span data-ttu-id="a0d4e-211">No espaço de trabalho **Biblioteca de Software**, expanda **Gerenciamento de Aplicativos** e escolha **Pacotes**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-211">In the **Software Library** workspace, expand **Application Management**, and then choose **Packages**.</span></span>  
  
3.  <span data-ttu-id="a0d4e-212">Na lista de pacotes, selecione o pacote criado e denominado **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-212">From the list of packages, select the package you created named **.NET Framework 4.5**.</span></span>  
  
4.  <span data-ttu-id="a0d4e-213">Na guia **Início**, no grupo **Implantação**, escolha **Implantar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-213">On the **Home** tab, in the **Deployment** group, choose **Deploy**.</span></span>  
  
5.  <span data-ttu-id="a0d4e-214">Na página **Geral** do **Assistente de Implantação de Software**, escolha **Procurar** e selecione a coleção anteriormente criada.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-214">On the **General** page of the **Deploy Software Wizard**, choose **Browse**, and then select the collection that you created earlier.</span></span> <span data-ttu-id="a0d4e-215">Escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-215">Choose **Next**.</span></span>  
  
6.  <span data-ttu-id="a0d4e-216">Na página **Conteúdo** do assistente, verifique se o ponto do qual você deseja distribuir o software é exibido e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-216">On the **Content** page of the wizard, verify that the point from which you want to distribute the software is displayed, and then choose **Next**.</span></span>  
  
7.  <span data-ttu-id="a0d4e-217">Na página **Configurações de Implantação** do assistente, confirme se a **Ação** está definida como **Instalar** e a **Finalidade** como **Obrigatório**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-217">On the **Deployment Settings** page of the wizard, confirm that **Action** is set to **Install**, and **Purpose** is set to **Required**.</span></span> <span data-ttu-id="a0d4e-218">Isso garantirá que o pacote de software seja uma instalação obrigatória nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-218">This ensures that the software package will be a mandatory installation on the targeted computers.</span></span> <span data-ttu-id="a0d4e-219">Escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-219">Choose **Next**.</span></span>  
  
8.  <span data-ttu-id="a0d4e-220">Na página **Agendamento** do assistente, especifique quando você deseja que o .NET Framework seja instalado.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-220">On the **Scheduling** page of the wizard, specify when you want the .NET Framework to be installed.</span></span> <span data-ttu-id="a0d4e-221">Você pode escolher **Nova** para atribuir uma hora de instalação ou instruir o software a ser instalado quando o usuário fizer logon, logoff ou assim que possível.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-221">You can choose **New** to assign an installation time, or instruct the software to install when the user logs on or off, or as soon as possible.</span></span> <span data-ttu-id="a0d4e-222">Escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-222">Choose **Next**.</span></span>  
  
9. <span data-ttu-id="a0d4e-223">Na página **Experiência do Usuário** do assistente, use os valores padrão e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-223">On the **User Experience** page of the wizard, use the default values and choose **Next**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="a0d4e-224">O ambiente de produção pode ter políticas que exijam diferentes seleções de agendamento de implantação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-224">Your production environment might have policies that require different selections for the deployment schedule.</span></span> <span data-ttu-id="a0d4e-225">Para obter informações sobre essas opções, consulte [Propriedades de nome de anúncio: guia Agendamento](http://technet.microsoft.com/library/bb694016.aspx) na Biblioteca TechNet.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-225">For information about these options, see [Advertisement Name Properties: Schedule Tab](http://technet.microsoft.com/library/bb694016.aspx) in the TechNet Library.</span></span>  
  
10. <span data-ttu-id="a0d4e-226">Na página **Pontos de Distribuição** do assistente, use os valores padrão e escolha **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-226">On the **Distribution Points** page of the wizard, use the default values and choose **Next**.</span></span>  
  
11. <span data-ttu-id="a0d4e-227">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-227">Complete the wizard.</span></span> <span data-ttu-id="a0d4e-228">Você pode monitorar o progresso da implantação no nó **Implantações** do espaço de trabalho **Monitoramento**.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-228">You can monitor the progress of the deployment in the **Deployments** node of the **Monitoring** workspace.</span></span>  
  
 <span data-ttu-id="a0d4e-229">O pacote agora será implantado na coleção de destino e a instalação silenciosa do .NET Framework 4.5 será iniciada.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-229">The package will now be deployed to the targeted collection and the silent installation of .NET Framework 4.5 will begin.</span></span> <span data-ttu-id="a0d4e-230">Para obter informações sobre códigos de erro de instalação do .NET Framework 4.5, consulte a seção [Códigos de retorno](#return_codes) posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-230">For information about .NET Framework 4.5 installation error codes, see the [Return Codes](#return_codes) section later in this topic.</span></span>  
  
<a name="resources"></a>   
## <a name="resources"></a><span data-ttu-id="a0d4e-231">Recursos</span><span class="sxs-lookup"><span data-stu-id="a0d4e-231">Resources</span></span>  
 <span data-ttu-id="a0d4e-232">Para obter mais informações sobre a infraestrutura para testar a implantação do pacote [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível, consulte os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-232">For more information about the infrastructure for testing the deployment of the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable package, see the following resources.</span></span>  
  
 <span data-ttu-id="a0d4e-233">**Active Directory, DNS, DHCP:**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-233">**Active Directory, DNS, DHCP:**</span></span>  
  
-   [<span data-ttu-id="a0d4e-234">Active Directory Domain Services para Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="a0d4e-234">Active Directory Domain Services for Windows Server 2008</span></span>](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [<span data-ttu-id="a0d4e-235">Servidor DNS</span><span class="sxs-lookup"><span data-stu-id="a0d4e-235">DNS Server</span></span>](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [<span data-ttu-id="a0d4e-236">Servidor DHCP</span><span class="sxs-lookup"><span data-stu-id="a0d4e-236">DHCP Server</span></span>](http://technet.microsoft.com/library/cc896553.aspx)  
  
 <span data-ttu-id="a0d4e-237">**SQL Server 2008:**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-237">**SQL Server 2008:**</span></span>  
  
-   [<span data-ttu-id="a0d4e-238">Instalando o SQL Server 2008 (vídeo do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="a0d4e-238">Installing SQL Server 2008 (SQL Server Video)</span></span>](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [<span data-ttu-id="a0d4e-239">Visão geral de segurança do SQL Server 2008 para administradores de banco de dados</span><span class="sxs-lookup"><span data-stu-id="a0d4e-239">SQL Server 2008 Security Overview for Database Administrators</span></span>](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 <span data-ttu-id="a0d4e-240">**System Center 2012 Configuration Manager (Ponto de Gerenciamento, Ponto de Distribuição):**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-240">**System Center 2012 Configuration Manager (Management Point, Distribution Point):**</span></span>  
  
-   [<span data-ttu-id="a0d4e-241">Administração de site do System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="a0d4e-241">Site Administration for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [<span data-ttu-id="a0d4e-242">Planejando e implantando site único do Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="a0d4e-242">Configuration Manager Single Site Planning and Deployment</span></span>](http://technet.microsoft.com/library/bb680961.aspx)  
  
 <span data-ttu-id="a0d4e-243">**Cliente do System Center 2012 Configuration Manager para computadores Windows:**</span><span class="sxs-lookup"><span data-stu-id="a0d4e-243">**System Center 2012 Configuration Manager client for Windows computers:**</span></span>  
  
-   [<span data-ttu-id="a0d4e-244">Implantação de clientes do System Center 2012 Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="a0d4e-244">Deploying Clients for System Center 2012 Configuration Manager</span></span>](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="a0d4e-245">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="a0d4e-245">Troubleshooting</span></span>  
  
### <a name="log-file-locations"></a><span data-ttu-id="a0d4e-246">Localizações dos arquivos de log</span><span class="sxs-lookup"><span data-stu-id="a0d4e-246">Log file locations</span></span>  
 <span data-ttu-id="a0d4e-247">Os seguintes arquivos de log são gerados durante a configuração do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-247">The following log files are generated during [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup:</span></span>  
  
 <span data-ttu-id="a0d4e-248">%temp%\Microsoft .NET Framework 4.5*.txt</span><span class="sxs-lookup"><span data-stu-id="a0d4e-248">%temp%\Microsoft .NET Framework 4.5*.txt</span></span>   
 <span data-ttu-id="a0d4e-249">%temp%\Microsoft .NET Framework 4.5\*.html</span><span class="sxs-lookup"><span data-stu-id="a0d4e-249">%temp%\Microsoft .NET Framework 4.5\*.html</span></span>  
  
 <span data-ttu-id="a0d4e-250">Você pode usar a [ferramenta de coleta de logs](http://www.microsoft.com/download/details.aspx?id=12493) para coletar os arquivos de log do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e criar um arquivo de gabinete compactado (.cab) que reduz o tamanho dos arquivos.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-250">You can use the [log collection tool](http://www.microsoft.com/download/details.aspx?id=12493) to collect the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] log files and to create a compressed cabinet (.cab) file that reduces the size of the files.</span></span>  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a><span data-ttu-id="a0d4e-251">Códigos de retorno</span><span class="sxs-lookup"><span data-stu-id="a0d4e-251">Return codes</span></span>  
 <span data-ttu-id="a0d4e-252">A tabela a seguir lista os códigos de retorno mais comuns do programa de instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-252">The following table lists the most common return codes from the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable installation program.</span></span> <span data-ttu-id="a0d4e-253">Os códigos de retorno são os mesmos para todas as versões do instalador.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-253">The return codes are the same for all versions of the installer.</span></span>  
  
 <span data-ttu-id="a0d4e-254">Para obter links para informações detalhadas, consulte a próxima seção [Códigos de erro de download](#additional_error_codes).</span><span class="sxs-lookup"><span data-stu-id="a0d4e-254">For links to detailed information, see the next section, [Download error codes](#additional_error_codes).</span></span>  
  
|<span data-ttu-id="a0d4e-255">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="a0d4e-255">Return code</span></span>|<span data-ttu-id="a0d4e-256">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0d4e-256">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a0d4e-257">0</span><span class="sxs-lookup"><span data-stu-id="a0d4e-257">0</span></span>|<span data-ttu-id="a0d4e-258">A instalação foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-258">Installation completed successfully.</span></span>|  
|<span data-ttu-id="a0d4e-259">1602</span><span class="sxs-lookup"><span data-stu-id="a0d4e-259">1602</span></span>|<span data-ttu-id="a0d4e-260">O usuário cancelou a instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-260">The user canceled installation.</span></span>|  
|<span data-ttu-id="a0d4e-261">1603</span><span class="sxs-lookup"><span data-stu-id="a0d4e-261">1603</span></span>|<span data-ttu-id="a0d4e-262">Ocorreu um erro fatal durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-262">A fatal error occurred during installation.</span></span>|  
|<span data-ttu-id="a0d4e-263">1641</span><span class="sxs-lookup"><span data-stu-id="a0d4e-263">1641</span></span>|<span data-ttu-id="a0d4e-264">É necessário reiniciar para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-264">A restart is required to complete the installation.</span></span> <span data-ttu-id="a0d4e-265">Esta mensagem indica êxito.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-265">This message indicates success.</span></span>|  
|<span data-ttu-id="a0d4e-266">3010</span><span class="sxs-lookup"><span data-stu-id="a0d4e-266">3010</span></span>|<span data-ttu-id="a0d4e-267">É necessário reiniciar para concluir a instalação.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-267">A restart is required to complete the installation.</span></span> <span data-ttu-id="a0d4e-268">Esta mensagem indica êxito.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-268">This message indicates success.</span></span>|  
|<span data-ttu-id="a0d4e-269">5100</span><span class="sxs-lookup"><span data-stu-id="a0d4e-269">5100</span></span>|<span data-ttu-id="a0d4e-270">O computador do usuário não atende aos requisitos do sistema.</span><span class="sxs-lookup"><span data-stu-id="a0d4e-270">The user's computer does not meet system requirements.</span></span>|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a><span data-ttu-id="a0d4e-271">Códigos de erro de download</span><span class="sxs-lookup"><span data-stu-id="a0d4e-271">Download error codes</span></span>  
  
-   [<span data-ttu-id="a0d4e-272">Códigos de erro do BITS (Serviço de Transferência Inteligente em Segundo Plano)</span><span class="sxs-lookup"><span data-stu-id="a0d4e-272">Background Intelligent Transfer Service (BITS) error codes</span></span>](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [<span data-ttu-id="a0d4e-273">Códigos de erro do moniker de URL</span><span class="sxs-lookup"><span data-stu-id="a0d4e-273">URL moniker error codes</span></span>](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [<span data-ttu-id="a0d4e-274">Códigos de erro WinHttp</span><span class="sxs-lookup"><span data-stu-id="a0d4e-274">WinHttp error codes</span></span>](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 <span data-ttu-id="a0d4e-275">Outros códigos de erro:</span><span class="sxs-lookup"><span data-stu-id="a0d4e-275">Other error codes:</span></span>  
  
-   [<span data-ttu-id="a0d4e-276">Códigos de erro do Windows Installer</span><span class="sxs-lookup"><span data-stu-id="a0d4e-276">Windows Installer error codes</span></span>](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [<span data-ttu-id="a0d4e-277">Códigos de resultado do Windows Update Agent</span><span class="sxs-lookup"><span data-stu-id="a0d4e-277">Windows Update Agent result codes</span></span>](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="a0d4e-278">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0d4e-278">See Also</span></span>  
 <span data-ttu-id="a0d4e-279">[Guia de implantação para desenvolvedores](../../../docs/framework/deployment/deployment-guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="a0d4e-279">[Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md) </span></span>  
 [<span data-ttu-id="a0d4e-280">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="a0d4e-280">System Requirements</span></span>](../../../docs/framework/get-started/system-requirements.md)

