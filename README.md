import java.awt.image.BufferedImage;
import java.io.IOException;
import javax.imageio.ImageIO;
import java.io.File;
import com.google.zxing.*;
import com.google.zxing.client.j2se.*;
import com.google.zxing.common.*;
import com.google.zxing.qrcode.*;

public class QRCodeScanner {
    public static void scanQRCode(String imagePath) {
        try {
            BufferedImage bufferedImage = ImageIO.read(new File(imagePath));
            LuminanceSource source = new BufferedImageLuminanceSource(bufferedImage);
            BinaryBitmap bitmap = new BinaryBitmap(new HybridBinarizer(source));
            Result result = new MultiFormatReader().decode(bitmap);
            System.out.println("QR Code Data: " + result.getText());
        } catch (NotFoundException e) {
            System.out.println("QR Code not found in image!");
        } catch (IOException e) {
            System.out.println("Error reading image file!");
        }
    }

    public static void main(String[] args) {
        String path = "C:/Users/YourUsername/Desktop/qr_sample.png";
        scanQRCode(path);
    }
}
# QR
To Scan a QR code
