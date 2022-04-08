# How to use editorconfig in vs code
It's an open source [project](https://editorconfig.org/) that makes sure you have the same settings in different editors. The editorconfig file (`.editorconfig`) has to be present in every project root. There's an extension for vs code that generates the file but you can manually edit/write it:
```config
# EditorConfig is awesome: https://EditorConfig.org

# top-most EditorConfig file
root = true

[*]
indent_style = space
indent_size = 4
end_of_line = crlf
charset = utf-8
trim_trailing_whitespace = false
insert_final_newline = false

[*.{cs,vb}]
dotnet_naming_rule.private_members_with_underscore.symbols  = private_fields
dotnet_naming_rule.private_members_with_underscore.style    = prefix_underscore
dotnet_naming_rule.private_members_with_underscore.severity = suggestion
 
dotnet_naming_symbols.private_fields.applicable_kinds           = field
dotnet_naming_symbols.private_fields.applicable_accessibilities = private
 
dotnet_naming_style.prefix_underscore.capitalization = camel_case
dotnet_naming_style.prefix_underscore.required_prefix = _
```