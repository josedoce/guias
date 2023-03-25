# Guias de ajuda

## wpf - Triggers
  ocê pode usar um MultiDataTrigger para verificar várias condições, incluindo o nome do estilo de um Button. Aqui está um exemplo:

xml
Copy code
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
Neste exemplo, definimos um estilo MyButtonStyle para o botão e um estilo para o TextBlock. O MultiDataTrigger no estilo TextBlock verifica duas condições: o nome do estilo do Button usando Style.TargetType.Name, e se o mouse está sobre o TextBlock usando IsMouseOver. Se ambas as condições forem atendidas, o Foreground do TextBlock é definido como branco.

Observe que as condições no MultiDataTrigger são verificadas em sequência, e todas as condições devem ser atendidas para que o Setter seja aplicado. Se você precisar de um comportamento diferente, pode ajustar as condições e valores conforme necessário.




Regenerate response
