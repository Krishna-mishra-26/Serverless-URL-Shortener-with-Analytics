# Serverless URL Shortener with Analytics


A feature-rich URL shortening service with advanced analytics capabilities, built with Node.js, Express, MongoDB, and vanilla JavaScript.




## Features

- **Custom URL Shortening**: Create shortened URLs with optional custom aliases
- **Secure Links**: Protect your links with password authentication
- **Expiration Control**: Set URLs to automatically expire after a specific time
- **QR Code Generation**: Generate QR codes for easy mobile sharing
- **Comprehensive Analytics Dashboard**:
  - Track clicks over time (daily/hourly)
  - Monitor geographic location of visitors
  - Analyze device types accessing your links
  - Identify referrer sources
  - Export analytics data as CSV
- **Real-time Click Tracking**: Monitor link performance with detailed metrics
- **Mobile-Responsive Design**: Works seamlessly on desktop and mobile devices



## **Sample Screenshots:**
<img src="https://github.com/user-attachments/assets/1104c221-56c7-47e5-b2fb-ad03c6900473" alt="HomePage-Index.html" height="500"/>

<img src="https://github.com/user-attachments/assets/4a29a537-c2a4-4305-9d7e-628e4e9df309" alt="HomePage-Index.html" height="500" width="400"/>


- URL Shortening Interface with QR code generation
- Analytics Dashboard with interactive charts
- Password-protected link access

## Tech Stack

### Backend
- **Node.js** & **Express.js**: Server-side framework
- **MongoDB** & **Mongoose**: Database and ODM
- **Shortid**: Generating unique URL identifiers
- **Bcrypt**: Password encryption for secure links
- **QRCode**: QR code generation
- **UAParser**: User agent detection for analytics

### Frontend
- **Vanilla JavaScript**: No frontend frameworks
- **Chart.js**: Data visualization
- **HTML5** & **CSS3**: Modern, responsive UI

## Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or cloud instance)

### Setup Instructions

1. **Clone the repository**
   ```bash
   gh repo clone Krishna-mishra-26/Serverless-URL-Shortener-with-Analytics
   cd url-shortener-project
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**  
   Create a `.env` file in the root directory with the following content:
   ```
   PORT=5000
   MONGO_URI=mongodb://127.0.0.1:27017/myURLShortener
   BASE_URL=http://localhost:5000
   ```
   - Adjust `MONGO_URI` to match your MongoDB connection string
   - Set `BASE_URL` to your server's URL (use `localhost` for local development)

4. **Start the server**
   ```bash
   npm start
   ```
   For development with auto-reload:
   ```bash
   npm run dev
   ```

5. **Access the application**  
   Open your browser and navigate to `http://localhost:5000`

## Project Structure

```
url-shortener-project/
├── backend/
│   ├── models/
│   │   ├── click.js      # Analytics data schema
│   │   └── url.js        # URL mapping schema
│   ├── routes/
│   │   └── api.js        # API endpoints
│   ├── utils/
│   │   └── generateQRCode.js  # QR code generation utility
│   └── server.js         # Backend server setup
├── client/
│   ├── css/
│   │   └── style.css     # Main stylesheet
│   ├── js/
│   │   ├── analytics.js  # Analytics dashboard functionality
│   │   └── main.js       # URL shortening functionality
│   ├── analytics.html    # Analytics dashboard page
│   └── index.html        # URL shortening page
├── server.js             # Main entry point
├── package.json
├── .env                  # Environment variables
README.md
```

## API Endpoints

### URL Management
- `POST /api/shorten` - Create a shortened URL
  - Accepts: `originalUrl`, `customAlias` (optional), `password` (optional), `expiresAt` (optional)
  - Returns: `shortUrl`, `qrCode` (base64)

- `GET /:shortId` - Redirect to original URL
  - Handles password authentication if required
  - Records click analytics

### Analytics
- `GET /:shortId/metadata` - Check if URL requires password
- `GET /api/analytics/:shortId` - Get analytics for a specific URL
- `GET /api/analytics/:shortId/export` - Export analytics data as CSV

## Deployment

This application requires server-side capabilities and cannot be deployed on static hosting platforms like GitHub Pages.

### Recommended Deployment Platforms

**DigitalOcean (Recommended)**
1. Create a DigitalOcean droplet with Node.js
2. Clone the repository to your droplet
3. Install dependencies: `npm install`
4. Install PM2: `npm install -g pm2`
5. Set up environment variables (update BASE_URL to your server's IP)
6. Start the application with PM2: `pm2 start server.js`
7. Set up a domain name and configure nginx (optional)

**Alternative Platforms:**
- **Render.com** - Free tier available, easy GitHub integration
- **Vercel** - Serverless deployment with good Node.js support
- **Heroku** - Popular platform with MongoDB add-ons
- **Railway** - Simple deployment with automatic HTTPS

### Important Configuration Note
⚠️ **For production deployment**: Update your `.env` file's `BASE_URL` from `http://localhost:5000` to your server's public IP address or domain name. Otherwise, shortened URLs won't work for external users.

Example:
```
BASE_URL=http://your-server-ip:5000
# OR
BASE_URL=https://yourdomain.com
```

## Future Enhancements

- User Authentication
- Custom domain support
- Advanced analytics features
- Social media integration
- Bulk URL creation
- API key support for programmatic access

## Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature-name`
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- [Chart.js](https://www.chartjs.org/) for the analytics visualizations
- [QRCode](https://www.npmjs.com/package/qrcode) for QR code generation
- [MongoDB](https://www.mongodb.com/) for reliable database solutions
- [Express.js](https://expressjs.com/) for the robust web framework

