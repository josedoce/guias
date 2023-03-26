# Guias de ajuda

## wpf - Triggers Multicondicional com e sem dados
  ocê pode usar um MultiDataTrigger para verificar várias condições, incluindo o nome do estilo de um Button. Aqui está um exemplo:

xml

```xml
<Window.Resources>
    <Style x:Key="MyButtonStyle" TargetType="Button">
        <Setter Property="Background" Value="Red" />
        <Setter Property="Foreground" Value="Black" />
    </Style>
    <Style TargetType="TextBlock">
        <Setter Property="Foreground" Value="Black" />
        <Style.Triggers>
            <MultiDataTrigger>
                <MultiDataTrigger.Conditions>
                    <Condition Binding="{Binding Path=Style.TargetType.Name, RelativeSource={RelativeSource AncestorType=Button}}" Value="MyButtonStyle" />
                    <Condition Binding="{Binding Path=IsMouseOver, RelativeSource={RelativeSource Self}}" Value="True" />
                </MultiDataTrigger.Conditions>
                <Setter Property="Foreground" Value="White" />
            </MultiDataTrigger>
        </Style.Triggers>
    </Style>
</Window.Resources>

<Grid>
    <Button Style="{StaticResource MyButtonStyle}" Content="Click me" />
    <TextBlock Text="Hello, world!" />
</Grid>
```
Neste exemplo, definimos um estilo MyButtonStyle para o botão e um estilo para o TextBlock. O MultiDataTrigger no estilo TextBlock verifica duas condições: o nome do estilo do Button usando Style.TargetType.Name, e se o mouse está sobre o TextBlock usando IsMouseOver. Se ambas as condições forem atendidas, o Foreground do TextBlock é definido como branco.

Observe que as condições no MultiDataTrigger são verificadas em sequência, e todas as condições devem ser atendidas para que o Setter seja aplicado. Se você precisar de um comportamento diferente, pode ajustar as condições e valores conforme necessário.




## wpf - usando triggers 

```xml
 <!--solução funcional
        http://mark-dot-net.blogspot.com/2007/07/creating-custom-wpf-button-template-in.html
        //como criar templates https://learn.microsoft.com/en-us/dotnet/desktop/wpf/controls/how-to-create-apply-template?view=netdesktop-7.0
    
        <ControlTemplate TargetType="Button"  x:Key="PrimaryButtonTemplate">
        <Border Name="border"
                       BorderThickness="1"
                       Padding="4,2"
                       BorderBrush="#0d6efd"
                       CornerRadius="3"
                       Background="{TemplateBinding Background}">
            <Grid ShowGridLines="True">
                <ContentPresenter 
                                HorizontalAlignment="Center"
                                VerticalAlignment="Center" 
                              
                                Name="contentShadow"
                                Style="{StaticResource ShadowStyle}">
                    <ContentPresenter.RenderTransform>
                        <TranslateTransform X="0.4" Y="0.4" />
                    </ContentPresenter.RenderTransform>
                </ContentPresenter>

                <ContentPresenter HorizontalAlignment="Center"
                           VerticalAlignment="Center" Name="content" Grid.Column="0"/>

            </Grid>
        </Border>
        
        <ControlTemplate.Triggers>
            <!-- 
            Multitriggers, ou seja, multigatilhos me permite adicionar como condicional varios gatilhos disparaados
            https://social.msdn.microsoft.com/Forums/vstudio/en-US/f6816293-e531-4c4a-ba2f-d32f37d17f55/is-it-possible-to-reuse-a-trigger-on-multiple-controls-easily?forum=wpf-->

    <Trigger Property="IsMouseOver" Value="True">

        <Setter Property="Button.Background" Value="{StaticResource primaryColorOver}"/>
        <Setter TargetName="border" Property="BorderBrush" Value="{StaticResource primaryColorOverBorder}" />
        <Setter Property="Foreground" Value="{StaticResource primaryColorOverFont}" />
    </Trigger>


    <Trigger Property="IsPressed" Value="True">
        
                            <Setter Property="Background" >
                                <Setter.Value>
                                    <SolidColorBrush Color="{StaticResource defaultColorPress}" />
                                    <LinearGradientBrush StartPoint="0,0" EndPoint="0,1" >
                                        <GradientStop Color="SpringGreen" Offset="0.35"/>
                                        <GradientStop Color="Green" Offset="0.95"/>
                                        <GradientStop Color="SpringGreen" Offset="0.25"/>
                                    </LinearGradientBrush>
                                    
                                </Setter.Value>
                            </Setter>
                                    
        <Setter Property="Background" Value="{StaticResource primaryColorPress}"/>
        <Setter TargetName="contentShadow" Property="RenderTransform" >
            <Setter.Value>
                <TranslateTransform Y="0.5" X="0.5" />
            </Setter.Value>
        </Setter>

    </Trigger>


    <Trigger Property="IsDefaulted" Value="True">
        <Setter TargetName="border" Property="BorderBrush" Value="#FF282828" />
    </Trigger>
    <Trigger Property="IsFocused" Value="True">
        <Setter TargetName="border" Property="BorderBrush" Value="#FF282828" />
    </Trigger>

    <Trigger Property="IsEnabled" Value="False">
        <Setter TargetName="border" Property="Opacity" Value="0.7" />
        <Setter Property="Foreground" Value="Gray" />
    </Trigger>


    </ControlTemplate.Triggers>
    </ControlTemplate>-->
    
```
