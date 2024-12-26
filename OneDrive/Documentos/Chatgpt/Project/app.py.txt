from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/calculate_crs', methods=['POST'])
def calculate_crs():
    data = request.json
    if not data:
        return jsonify({"error": "No data provided"}), 400

    # Ejemplo simple de cálculo CRS
    age = data.get("age", 0)
    education = data.get("education", "").lower()

    points = 0
    if 18 <= age <= 35:
        points += 100
    if education == "bachelor":
        points += 120

    return jsonify({"score": points, "details": {"age_points": 100, "education_points": 120}})

if __name__ == '__main__':
    app.run(debug=True)
