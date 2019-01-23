---
title: 'Como: Validar configurações do aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
ms.openlocfilehash: 6ebdf1ee74e3ed41b02fdeb545ffc57aaa2d6d7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496277"
---
# <a name="how-to-validate-application-settings"></a><span data-ttu-id="e6158-102">Como: Validar configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e6158-102">How to: Validate Application Settings</span></span>
<span data-ttu-id="e6158-103">Este tópico demonstra como validar configurações do aplicativo antes que elas sejam persistentes.</span><span class="sxs-lookup"><span data-stu-id="e6158-103">This topic demonstrates how to validate application settings before they are persisted.</span></span>  
  
 <span data-ttu-id="e6158-104">Considerando que as configurações do aplicativo são fortemente tipadas, você tem alguma confiança de que os usuários não podem atribuir dados de um tipo incorreto a uma determinada configuração.</span><span class="sxs-lookup"><span data-stu-id="e6158-104">Because application settings are strongly typed, you have some confidence that users cannot assign data of an incorrect type to a given setting.</span></span> <span data-ttu-id="e6158-105">No entanto, um usuário ainda pode tentar atribuir um valor a uma configuração que esteja fora do limite aceitável, por exemplo, fornecendo uma data de nascimento no futuro.</span><span class="sxs-lookup"><span data-stu-id="e6158-105">However, a user still may attempt to assign a value to a setting that falls outside of acceptable bounds—for example, supplying a birth date that occurs in the future.</span></span> <span data-ttu-id="e6158-106"><xref:System.Configuration.ApplicationSettingsBase>, a classe pai de todas as classes de configurações do aplicativo, expõe quatro eventos para permitir essa verificação de limites.</span><span class="sxs-lookup"><span data-stu-id="e6158-106"><xref:System.Configuration.ApplicationSettingsBase>, the parent class of all application settings classes, exposes four events to enable such bounds checking.</span></span> <span data-ttu-id="e6158-107">Manipular esses eventos coloca todo o código de validação em um único local, em vez de distribuí-lo em todo o projeto.</span><span class="sxs-lookup"><span data-stu-id="e6158-107">Handling these events puts all of your validation code in a single location, rather than scattering it throughout your project.</span></span>  
  
 <span data-ttu-id="e6158-108">O evento que você usa depende de quando você precisa validar suas configurações, conforme descrito na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6158-108">The event you use depends upon when you need to validate your settings, as described in the following table.</span></span>  
  
|<span data-ttu-id="e6158-109">evento</span><span class="sxs-lookup"><span data-stu-id="e6158-109">Event</span></span>|<span data-ttu-id="e6158-110">Ocorrência e uso</span><span class="sxs-lookup"><span data-stu-id="e6158-110">Occurrence and use</span></span>|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|<span data-ttu-id="e6158-111">Ocorre após o carregamento inicial de um grupo de propriedades de configurações.</span><span class="sxs-lookup"><span data-stu-id="e6158-111">Occurs after the initial loading of a settings property group.</span></span><br /><br /> <span data-ttu-id="e6158-112">Use esse evento para validar valores iniciais para todo o grupo de propriedades antes que eles sejam usados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e6158-112">Use this event to validate initial values for the entire property group before they are used within the application.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|<span data-ttu-id="e6158-113">Ocorre antes da alteração do valor de uma única propriedade.</span><span class="sxs-lookup"><span data-stu-id="e6158-113">Occurs before the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="e6158-114">Use esse evento para validar uma única propriedade antes que ela seja alterada.</span><span class="sxs-lookup"><span data-stu-id="e6158-114">Use this event to validate a single property before it is changed.</span></span> <span data-ttu-id="e6158-115">Pode fornecer imediatamente comentários aos usuários sobre suas ações e escolhas.</span><span class="sxs-lookup"><span data-stu-id="e6158-115">It can provide immediate feedback to users regarding their actions and choices.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|<span data-ttu-id="e6158-116">Ocorre depois da alteração de uma única propriedade de configurações.</span><span class="sxs-lookup"><span data-stu-id="e6158-116">Occurs after the value of a single settings property is changed.</span></span><br /><br /> <span data-ttu-id="e6158-117">Use esse evento para validar uma única propriedade depois que ela for alterada.</span><span class="sxs-lookup"><span data-stu-id="e6158-117">Use this event to validate a single property after it is changed.</span></span> <span data-ttu-id="e6158-118">Este evento raramente é usado para validação, a menos que um processo de validação longo e assíncrono seja necessário.</span><span class="sxs-lookup"><span data-stu-id="e6158-118">This event is rarely used for validation unless a lengthy, asynchronous validation process is required.</span></span>|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|<span data-ttu-id="e6158-119">Ocorre antes que o grupo de propriedades de configurações seja armazenado.</span><span class="sxs-lookup"><span data-stu-id="e6158-119">Occurs before the settings property group is stored.</span></span><br /><br /> <span data-ttu-id="e6158-120">Use esse evento para validar valores para todo o grupo de propriedades antes que elas sejam persistentes no disco.</span><span class="sxs-lookup"><span data-stu-id="e6158-120">Use this event to validate values for the entire property group before they are persisted to disk.</span></span>|  
  
 <span data-ttu-id="e6158-121">Normalmente, você não usará todos esses eventos dentro do mesmo aplicativo para fins de validação.</span><span class="sxs-lookup"><span data-stu-id="e6158-121">Typically, you will not use all of these events within the same application for validation purposes.</span></span> <span data-ttu-id="e6158-122">Por exemplo, muitas vezes é possível atender a todos os requisitos de validação manipulando somente o <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> eventos.</span><span class="sxs-lookup"><span data-stu-id="e6158-122">For example, it is often possible to fulfill all validation requirements by handling only the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
 <span data-ttu-id="e6158-123">Um manipulador de eventos geralmente executa uma das seguintes ações quando detecta um valor inválido:</span><span class="sxs-lookup"><span data-stu-id="e6158-123">An event handler generally performs one of the following actions when it detects an invalid value:</span></span>  
  
-   <span data-ttu-id="e6158-124">Fornece automaticamente um valor sabidamente correto, como o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="e6158-124">Automatically supplies a value known to be correct, such as the default value.</span></span>  
  
-   <span data-ttu-id="e6158-125">Consulta novamente o usuário do código do servidor para obter informações.</span><span class="sxs-lookup"><span data-stu-id="e6158-125">Re-queries the user of server code for information.</span></span>  
  
-   <span data-ttu-id="e6158-126">Para eventos gerados antes de suas ações associadas, como <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> e <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, usa o <xref:System.ComponentModel.CancelEventArgs> argumento para cancelar a operação.</span><span class="sxs-lookup"><span data-stu-id="e6158-126">For events raised before their associated actions, such as <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> and <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>, uses the <xref:System.ComponentModel.CancelEventArgs> argument to cancel the operation.</span></span>  
  
 <span data-ttu-id="e6158-127">Para obter mais informações sobre a manipulação de eventos, consulte [Visão geral de manipuladores de evento](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e6158-127">For more information about event handling, see [Event Handlers Overview](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="e6158-128">Os procedimentos a seguir mostram como testar uma data de nascimento é válida usando o <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> ou o <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> eventos.</span><span class="sxs-lookup"><span data-stu-id="e6158-128">The following procedures show how to test for a valid birth date using either the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> or the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span> <span data-ttu-id="e6158-129">Os procedimentos foram escritos com a pressuposição de que você já criou suas configurações do aplicativo. Neste exemplo, vamos executar a verificação de limites em uma configuração chamada `DateOfBirth`.</span><span class="sxs-lookup"><span data-stu-id="e6158-129">The procedures were written under the assumption that you have already created your application settings; in this example, we will perform bounds checking on a setting named `DateOfBirth`.</span></span> <span data-ttu-id="e6158-130">Para obter mais informações sobre a criação de configurações, consulte [como: Criar configurações de aplicativo](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e6158-130">For more information about creating settings, see [How to: Create Application Settings](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).</span></span>  
  
### <a name="to-obtain-the-application-settings-object"></a><span data-ttu-id="e6158-131">Para obter o objeto de configurações do aplicativo</span><span class="sxs-lookup"><span data-stu-id="e6158-131">To obtain the application settings object</span></span>  
  
-   <span data-ttu-id="e6158-132">Obtenha uma referência para o objeto de configurações de aplicativo (a instância do wrapper) executando um dos seguintes itens com marcadores:</span><span class="sxs-lookup"><span data-stu-id="e6158-132">Obtain a reference to the application settings object (the wrapper instance) by completing one of the following bulleted items:</span></span>  
  
    -   <span data-ttu-id="e6158-133">Se você tiver criado suas configurações usando a caixa de diálogo de Configurações de aplicativo do Visual Studio no **Editor de propriedade**, poderá recuperar o objeto de configurações padrão gerado para sua linguagem por meio da seguinte expressão.</span><span class="sxs-lookup"><span data-stu-id="e6158-133">If you created your settings using the Visual Studio Application Settings dialog box in the **Property Editor**, you can retrieve the default settings object generated for your language through the following expression.</span></span>  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         <span data-ttu-id="e6158-134">-ou-</span><span class="sxs-lookup"><span data-stu-id="e6158-134">-or-</span></span>  
  
    -   <span data-ttu-id="e6158-135">Se você for um desenvolvedor de Visual Basic e tiver criado as configurações do aplicativo usando o Designer de Projeto, poderá recuperar as configurações usando o [Objeto My.Settings](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="e6158-135">If you are a Visual Basic developer and you created your application settings using the Project Designer, you can retrieve your settings by using the [My.Settings Object](~/docs/visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
         <span data-ttu-id="e6158-136">-ou-</span><span class="sxs-lookup"><span data-stu-id="e6158-136">-or-</span></span>  
  
    -   <span data-ttu-id="e6158-137">Se você tiver criado suas configurações derivando de <xref:System.Configuration.ApplicationSettingsBase> diretamente, você precisa instanciar sua classe manualmente.</span><span class="sxs-lookup"><span data-stu-id="e6158-137">If you created your settings by deriving from <xref:System.Configuration.ApplicationSettingsBase> directly, you need to instantiate your class manually.</span></span>  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 <span data-ttu-id="e6158-138">Os procedimentos a seguir foram escritos com a suposição de que o objeto de configurações do aplicativo foi obtido concluindo o último item com marcadores neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="e6158-138">The following procedures were written under the assumption that the application settings object was obtained by completing the last bulleted item in this procedure.</span></span>  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a><span data-ttu-id="e6158-139">Para validar as Configurações do Aplicativo quando uma configuração é alterada</span><span class="sxs-lookup"><span data-stu-id="e6158-139">To validate Application Settings when a setting is changing</span></span>  
  
1.  <span data-ttu-id="e6158-140">Se você estiver um C# developer, no seu formulário ou do controle `Load` evento, adicione um manipulador de eventos para o <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> evento.</span><span class="sxs-lookup"><span data-stu-id="e6158-140">If you are a C# developer, in your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> event.</span></span>  
  
     <span data-ttu-id="e6158-141">-ou-</span><span class="sxs-lookup"><span data-stu-id="e6158-141">-or-</span></span>  
  
     <span data-ttu-id="e6158-142">Se você for um desenvolvedor de Visual Basic, deverá declarar a variável `Settings` usando a palavra-chave `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="e6158-142">If you are a Visual Basic developer, you should declare the `Settings` variable using the `WithEvents` keyword.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  <span data-ttu-id="e6158-143">Defina o manipulador de eventos e escreva o código dentro dele para executar a verificação de limites na data de nascimento.</span><span class="sxs-lookup"><span data-stu-id="e6158-143">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a><span data-ttu-id="e6158-144">Para validar as Configurações do Aplicativo quando uma operação de Salvar ocorrer</span><span class="sxs-lookup"><span data-stu-id="e6158-144">To validate Application Settings when a Save occurs</span></span>  
  
1.  <span data-ttu-id="e6158-145">No seu formulário ou do controle `Load` evento, adicione um manipulador de eventos para o <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> eventos.</span><span class="sxs-lookup"><span data-stu-id="e6158-145">In your form or control's `Load` event, add an event handler for the <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> event.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  <span data-ttu-id="e6158-146">Defina o manipulador de eventos e escreva o código dentro dele para executar a verificação de limites na data de nascimento.</span><span class="sxs-lookup"><span data-stu-id="e6158-146">Define the event handler, and write the code inside of it to perform bounds checking on the birth date.</span></span>  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6158-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6158-147">See also</span></span>
- [<span data-ttu-id="e6158-148">Criando manipuladores de eventos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6158-148">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="e6158-149">Como: Criar configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="e6158-149">How to: Create Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
