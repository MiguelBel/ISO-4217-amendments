# ISO-4217 Amendments

I didn't find a way to see all the amendments of the ISO-4217 (currencies) so I gathered from the 6 to the 162. The ones I found.

The script I used is:

```
require 'open-uri'

def save_amendment(id)
  url = "http://www.currency-iso.org/dam/isocy/downloads/dl_currency_iso_amendment_#{id}.pdf"

  begin
    open("amendments/#{id}.pdf", 'wb') do |file|
      file << open(url).read
    end
  rescue => e
    p "[FAIL] Amendment #{id}, failed to download #{e}"
  end

  p "[SUCCESS] Amendment #{id}, good to go"
end

(6..162).each do |amendment_number|
  save_amendment(amendment_number)
end
```