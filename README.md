# xmlvalidation
# to validate xml files against xsd schema files
!pip install xmlschema
!pip install lxml
from google.colab import files
import xmlschema
from lxml import etree

# Upload XML files
uploaded_xml = files.upload()

# Upload XSD files
uploaded_xsd = files.upload()

# Get the content of uploaded XML and XSD files
xml_file_content = next(iter(uploaded_xml.values())).decode('utf-8')
xsd_file_content = next(iter(uploaded_xsd.values())).decode('utf-8')

# Get the content of uploaded XML and XSD files
xml_file_content = next(iter(uploaded_xml.values())).decode('utf-8')
xsd_file_content = next(iter(uploaded_xsd.values())).decode('utf-8')

# Validation check of xml against xsd
try:
    schema = xmlschema.XMLSchema(xsd_file_content)
    schema.validate(xml_file_content)
    print("Validation successful: The XML is valid against the XSD.")
except xmlschema.XMLSchemaValidationError as e:
    print("Validation failed: The XML is not valid against the XSD.")
    print("Validation errors:")
    print(str(e))
except Exception as e:
    print("An error occurred:", str(e))

# Xml files should be well-formatted and hence can be checked if they adhere to a specific xsd
